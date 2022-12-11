cmake_minimum_required(VERSION 3.16)
project(myproject LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

set(CMAKE_CXX_STANDARD 17)

file(GLOB cpp_sources ${PROJECT_SOURCE_DIR}/src/*.cpp)
add_library(mylib ${cpp_sources})
target_include_directories(mylib PUBLIC ${PROJECT_SOURCE_DIR}/inc)

include(FetchContent)
include(ExternalProject)
include(cmake/options.cmake)

if (ENABLE_TESTING)
  add_subdirectory(tests)
endif()
