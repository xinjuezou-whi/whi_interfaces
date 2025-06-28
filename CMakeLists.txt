cmake_minimum_required(VERSION 3.5)
project(whi_interfaces)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(actionlib_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(moveit_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/WhiBattery.msg"
  "msg/WhiBoundingBox.msg"
  "msg/WhiBoundingBoxes.msg"
  "msg/WhiEng.msg"
  "msg/WhiIndicator.msg"
  "msg/WhiJointPose.msg"
  "msg/WhiLineChart2D.msg"
  "msg/WhiMotionState.msg"
  "msg/WhiPartialDischarge.msg"
  "msg/WhiRcState.msg"
  "msg/WhiTaskState.msg"
  "msg/WhiTcpPose.msg"
  "msg/WhiTemperatureHumidity.msg"
  "msg/WhiVectorFloat.msg"
  "srv/WhiSrvArmEncoder.srv"
  "srv/WhiSrvCurrentTcpPose.srv"
  "srv/WhiSrvDepth.srv"
  "srv/WhiSrvIndicator.srv"
  "srv/WhiSrvIo.srv"
  "srv/WhiSrvJointNames.srv"
  "srv/WhiSrvJointPose.srv"
  "srv/WhiSrvMotionOffsets.srv"
  "srv/WhiSrvPartialDischarge.srv"
  "srv/WhiSrvQrcode.srv"
  "srv/WhiSrvTcpDifference.srv"
  "srv/WhiSrvTcpPose.srv"
  "srv/WhiSrvTemperatureHumidity.srv"
  "action/PoseRegistration.action"
  DEPENDENCIES std_msgs
  DEPENDENCIES geometry_msgs
  DEPENDENCIES action_msgs
  DEPENDENCIES moveit_msgs
 )

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
