
cmake_minimum_required(VERSION 3.10)

# set the project name
project(FirstCMake VERSION 1.0)

# set options
option(FIRSTCMAKE_WITH_EXECUTABLES "Compile mains" OFF)
option(FIRSTCMAKE_WITH_TESTS "Compile test projects" OFF)

#export configuration to source code
configure_file(cmake/FirstCMakeConfig.h.in FirstCMakeConfig.h)

#about libraries
add_subdirectory(src/log_lib)

#about executable
if(FIRSTCMAKE_WITH_EXECUTABLES)
    # Enable testing with CTest
    message(STATUS "Configuring FirstCMake with executables")
    add_subdirectory(mains)
endif()

#about tests
if(FIRSTCMAKE_WITH_TESTS)
    # Enable testing with CTest
    enable_testing()
    message(STATUS "Configuring FirstCMake with tests")
    add_subdirectory(tests)
endif()
