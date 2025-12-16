cmake_minimum_required(VERSION 3.22)
project(binaryfileanalyzer)

# Setting to C++17 bc GoogleTest requires it
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED, ON)

# Telling CMAKE that GTEST is a required dependency and to fetch or download it
include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip #update this url
)

FetchContent_MakeAvailable(googletest)

#building main binary
add_executable(${PROJECT_NAME} ./src/main.cpp)

#building out tests
enable_testing()

add_executable(hello_test ./tests/test.cpp)
target_link_libraries(hello_test GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(hello_test)