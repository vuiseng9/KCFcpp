cmake_minimum_required(VERSION 2.8)
project(test)

set(OpenCV_DIR /opt/ocv/lib/cmake/opencv4)
find_package(OpenCV REQUIRED)
if(OpenCV_FOUND)
    message("OPENCV Found")
else()
    message("Failed to find OpenCV")
    return()
endif()

if(NOT WIN32)
ADD_DEFINITIONS("-std=c++0x -O3")
endif(NOT WIN32)

include_directories(src) 
FILE(GLOB_RECURSE sourcefiles "src/*.cpp")
add_executable( KCF ${sourcefiles} )
link_directories(/opt/ocv/lib)
target_link_libraries( KCF ${OpenCV_LIBS})




