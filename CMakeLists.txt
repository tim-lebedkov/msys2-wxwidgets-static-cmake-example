cmake_minimum_required(VERSION 2.8.12)
project(wxwidgets-cmake-example)

if(NOT MSVC)
  SET(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} -Wl,-Map,${PROJECT_NAME}.map")
  SET(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -static-libstdc++ -static-libgcc -static -g -Os")
endif()

# build should fail when compiler don't support standard defined by CMAKE_CXX_STANDARD
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_STANDARD 11)


#set(wxWidgets_FIND_STYLE "win32")
#set(wxWidgets_CONFIGURATION mswu)
#find_package(wxWidgets REQUIRED)
#include(${wxWidgets_USE_FILE})

add_executable(wxwidgets-cmake-example "src/main.cpp")

#set_property(TARGET wxwidgets-cmake-example PROPERTY INTERPROCEDURAL_OPTIMIZATION TRUE)

target_include_directories(wxwidgets-cmake-example PRIVATE "C:/msys64/mingw64/include/wx-3.0")
target_include_directories(wxwidgets-cmake-example PRIVATE "C:/msys64/mingw64/lib/wx/include/msw-unicode-static-3.0")

target_link_libraries(wxwidgets-cmake-example
    wx_mswu_core-3.0
    wx_baseu-3.0
    comctl32
    uuid
    oleacc
    png
    z)

#target_link_libraries(wxwidgets-cmake-example ${wxWidgets_LIBRARIES})
