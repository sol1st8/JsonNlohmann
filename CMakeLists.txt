cmake_minimum_required(VERSION 3.11)

project(json CXX)
set(CMAKE_CXX_STANDARD 17)

include(${CMAKE_BINARY_DIR}/conanbuildinfo_multi.cmake)
conan_basic_setup(TARGETS)

add_executable(json main.cpp)

if(CMAKE_SYSTEM_NAME MATCHES "^MINGW")
  set(SYSTEM_LIBS -lstdc++)
else()
  set(SYSTEM_LIBS)
endif()

target_include_directories(json PRIVATE CONAN_PKG::nlohmann_json)
target_link_libraries(json CONAN_PKG::nlohmann_json)
target_link_libraries(json ${SYSTEM_LIBS})
