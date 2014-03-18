project(BING)
cmake_minimum_required(VERSION 2.8)

set(3RDPARTY_DIR /home/songzheng/ssd/usr/songzheng/weardex-algorithm/3rdParty)

set(CXX_COMMON_FLAGS "-fPIC -Wno-deprecated-declarations -msse4 -DUSE_SSE -std=c++11")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -gdwarf-3")

include_directories(${3RDPARTY_DIR}/opencv_2461/include)

file(GLOB SRC_LIST Objectness/*.cpp Objectness/*.h)
file(GLOB LIBLINEAR_LIST LibLinear/*.cpp LibLinear/*.h)

add_library(BING SHARED ${SRC_LIST} ${LIBLINEAR_LIST})
target_link_libraries(BING opencv_imageproc opencv_highgui opencv_core tiff jpeg png jasper z rt)

add_executable(test_voc test/test_voc.cpp)
