# Use the osrf/ros:noetic-desktop-full-focal as the base image
FROM osrf/ros:noetic-desktop-full-focal

# Set the working directory to /workspace
WORKDIR /workspace

# Create a catkin workspace
RUN mkdir -p /workspace/catkin_ws/src

# install Git
RUN apt-get update && apt-get install -y \
    git

# Clone the dev_container_demo repository into the workspace
RUN git clone https://github.com/rfzeg/dev_container_demo.git /workspace/catkin_ws/src/dev_container_demo

# Install dependencies
RUN apt-get update && apt-get install -y \
    python3-rosdep \
    && rm -rf /var/lib/apt/lists/*

# Set up catkin workspace
RUN /bin/bash -c "source /opt/ros/noetic/setup.bash && \
    cd /workspace/catkin_ws && \
    catkin_make"

# Set the entry point to start a bash shell
CMD ["/bin/bash"]