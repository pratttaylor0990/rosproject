cmake_minimum_required(VERSION 2.8.3)
project(taylor_ros)

## Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS 
 roscpp 
 rospy 
 std_msgs 
 message_generation
)

## Declare ROS messages and services
add_message_files(FILES Num.msg)
add_service_files(FILES AddTwoInts.srv)

## Generate added messages and services
generate_messages(DEPENDENCIES std_msgs)

## Declare a catkin package
catkin_package()

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(laserScan src/laserScan.cpp)

add_dependencies(laserScan taylor_ros_generate_messages_cpp)
target_link_libraries(laserScan ${catkin_LIBRARIES})

##add_executable(move src/move.cpp)
##target_link_libraries(move ${catkin_LIBRARIES})
