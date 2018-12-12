# ABB Experimental - but with my changes

## The changes

This package was written for both the 1.2 meter variant as well as the 1.45 meter variant in mind. The problem is that they did not actually create the .urdf model and .stl model for the 1.45 meter variant. This original repo is also missing the edits I created for the tutorial for WPI's ABB 1600 1.45 variant, so I have decided to just fork this repo and make the changes on this version instead of the original version. This version corresponds to the tutorial that I wrote, so, in case I missed something, the user should not have to edit any of the files that I mention in that tutorial.

### Files edited from the original repository for branch kinetic-devel
```
abb_experimental/abb_irb1600_6_12_moveit_config/launch/trajectory_execution.launch.xml
abb_experimental/abb_irb1600_6_12_moveit_config/launch/moveit_planning_execution.launch
abb_experimental/abb_irb1600_support/launch/robot_interface_download_irb1600_6_12.launch
```
Then, these are the .urdf (.xacro) and .stl files that need to be edited:
```
abb_experimental/abb_irb1600_support/urdf/irb1600_6_12_macro.xacro
abb_experimental/abb_irb1600_support/meshes/irb1600_6_12/collision/link_2.stl
abb_experimental/abb_irb1600_support/meshes/irb1600_6_12/visual/link_2.stl
```

The first 3 files I edited myself. I left the original files alone and appended a `_original` to the end of the filename. The second 3 files will need to be looked at more in depth. The .xacro file can be modified for the longer link 2, but that does not fix the collisions and visualization. Those need to be fixed by an .stl file editor.

This [is the link](https://new.abb.com/products/robotics/industrial-robots/irb-1600/irb-1600-data) that contains robot dimensions for the corrected .xacro file.

I have also copied the version of the manual that I am referencing into this repo.

# The Original Docs

[![support level: community](https://img.shields.io/badge/support%20level-community-lightgray.png)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)

[ROS-Industrial][] ABB experimental meta-package.  See the [ROS wiki][] page for more information.


## Contents

This repository contains packages that will be migrated to the [abb][] repository after they have received sufficient testing.
The contents of these packages are subject to change, without prior notice.
Any available APIs are to be considered unstable and are not guaranteed to be complete and / or functional.


## Build
### Build from Source (developers only, not recommended)
This build methods uses:
 - [wstool][] for rosinstall.
 - [catkin tools][] for building.
This package depends on the following ros dependencies that are not included in the source build method, so they will need to be installed:
```
sudo apt install ros-kinetic-industrial-core ros-kinetic-moveit
```
Now build the abb_experimental package:
```
mkdir -p abb_experimental_ws/src
cd abb_experimental_ws/src
git clone -b kinetic-devel git@github.com:ros-industrial/abb_experimental.git
wstool init .
wstool merge abb_experimental/abb_experimental.rosinstall
wstool update
catkin build
```

[ROS-Industrial]: http://wiki.ros.org/Industrial
[ROS wiki]: http://wiki.ros.org/abb_experimental
[abb]: https://github.com/ros-industrial/abb
[wstool]: http://wiki.ros.org/wstool
[catkin tools]: https://catkin-tools.readthedocs.io/en/latest/
