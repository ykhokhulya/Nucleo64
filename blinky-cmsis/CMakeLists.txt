cmake_minimum_required(VERSION 2.8)

project(blinky-cmsis)
enable_language(ASM)

list(APPEND CMAKE_MODULE_PATH ../stm32-cmake/cmake)

find_package(CMSIS REQUIRED)

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMSIS_INCLUDE_DIRS}
    ${STM32HAL_INCLUDE_DIR})

file(GLOB_RECURSE PROJECT_SOURCES *.c)

add_executable(
    ${PROJECT_NAME}
    ${PROJECT_SOURCES}
    ${CMSIS_SOURCES})

stm32_set_target_properties(${PROJECT_NAME})
stm32_add_hex_bin_targets(${PROJECT_NAME})
stm32_print_size_of_targets(${PROJECT_NAME})
