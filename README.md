# ros2
conduct simulation and bringup using ur+robotiq gripper
ros2 launch my_robot_simulation sim_moveit.launch.py world_file:="/ros2_ws/src/my_packages/my_robot_simulation/worlds/my_world2.sdf"
cd src/rosboard&&./run


ros2 action send_goal /robotiq_gripper_controller/follow_joint_trajectory control_msgs/action/FollowJointTrajectory "{
  trajectory: {
    joint_names: ['robotiq_85_left_knuckle_joint'],
    points: [
      {
        positions: [0.5],
        velocities: [0.1],
        effort: [100.0],
        time_from_start: {sec: 1, nanosec: 0}
      }
    ]
  }
}"

キャリブれーしょんのローンチはブリングアップのconfigでおこなう。
pcはwebをひらいてOPEncnnect　、dockerは以下を行う
 sudo apt-get update&& sudo apt-get install ros-jazzy-foxglove-bridge
  ros2 run foxglove_bridge foxglove_bridge