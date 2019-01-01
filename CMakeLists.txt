cmake_minimum_required(VERSION 2.8.12)
project(fcl_ros)

add_compile_options(-std=c++11 -w)

find_package( catkin REQUIRED COMPONENTS )

set(FCL_BUILD_TESTS OFF CACHE BOOL "Disable FCL tests")
set(BUILD_TESTING OFF CACHE BOOL "Disable FCL tests")

file( MAKE_DIRECTORY "${CMAKE_INSTALL_PREFIX}/include/fcl" )

find_package(PkgConfig)
pkg_check_modules(PC_CCD ccd)

catkin_package( 
  INCLUDE_DIRS fcl/include ${CMAKE_INSTALL_PREFIX}/include/fcl
  LIBRARIES fcl
  DEPENDS PC_CCD )

add_subdirectory(fcl)
