cmake_minimum_required(VERSION 3.5)
project(navigation_interfaces)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(action_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/ComputePathToPose.action"
  "action/NavigateToPose.action"
  "action/FollowWaypoints.action"
  "action/Spin.action"
  "action/Wait.action"
  "msg/Aabb.msg"
  "msg/BoundingVolume.msg"
  "msg/Frustum.msg"
  "msg/LineSegment.msg"
  "msg/Obb.msg"
  "msg/Plane.msg"
  "msg/Point.msg"
  "msg/Ray.msg"
  "msg/Sphere.msg"
  "msg/UfoMapMetaData.msg"
  "msg/UfoMap.msg"
  "msg/UfoMapStamped.msg"
  "srv/LoadMap.srv"
  "srv/Reset.srv"
  "srv/SaveMap.srv"
  "srv/Mission.srv"
  DEPENDENCIES builtin_interfaces geometry_msgs std_msgs action_msgs nav_msgs
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
