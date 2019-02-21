2. **DBW node**

   DBWNode subscribes to the current velocity and way points that are published by waypoint_updator node. These topics are then processed using the two control logics below to determine the final throttle, steering and brake ratio, to maneuver the vehicle smoothly along the waypoints. 

    - Subscribes to topics: `/current velocity`, `/twist_cmd`, `/dbw_enabled`
    - Publishes to topics: `/steering_com`, `/throttle_cmd`, `/brake_cmd` 	

   

   DBW node then processes vehicle's throttle/brake and steering control using models below

   - twist_control.py: vehicle throttle control using PID and low-pass filter 
   - yaw_control.py: steering control with a  simple vehicle dynamics model and linear/angular velocity

   

   We've set the proportional, integral, and differential values for PID as below.

| Type              | Value |
| ----------------- | ----- |
| Proportional (Kp) | 0.2   |
| Integral (Ki)     | 0.002 |
| Differential (Kd) | 0.005 |