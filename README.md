# Robot-Dynamics-and-Control_Dynamic-Robot-Control-through-Simulink
The assignment is about the Dynamic Control of a manipulator using Matlab
and Simulink.The packages used for the work are "Robotics Systems Toolbox"
, "Simscape Multibody" and "Robot Library Data Support Package".We are
given with a simple simulation model of a UR5 robot and are supposed to
control it providing the torque commands to the joints.

__INTRODUCTION__

In this assignment, we are working on providing the torque commands to the joints to control a
UR5 robot.The accuracy of dynamic parameters plays an major role in the precision, performance
and robustness of these control algorithms. Moreover, a deep knowledge of the dynamic parameters
is needed in path planning algorithms that take into account robot dynamics. Especially in
the mechatronics area of robotics, model-based control is crucial for the increase of the system
precision and reliability.The toolboxes used for the proposed work are Robotic Systems Toolbox
, Simscape Multibody and Robot Library Data Support Package.This support package provides
source mesh visualization and helps in getting a clear idea of the happenings.

![UR5](https://user-images.githubusercontent.com/93926797/189098799-43551b88-b733-4927-a006-abf90f80f78e.JPG)

__METHODOLOGY__

##### GRAVITY COMPENSATION

In the first exercise, we are focused on giving a gravity compensation to the robot so that it
doesn’t fall due to gravity and remains intact without changing it’s configuration.So our main
focus is to make sure that we provide a block in the simulink file (as shown in the figure below)
that will compensate the gravity and prevent the robot from making a free-fall due to gravity
and remains intact. The only thing that we need to keep in mind is that the robot does not lose
it’s configuration.
![ex1bd](https://user-images.githubusercontent.com/93926797/189100416-6cc447fe-ae6c-42f1-87b7-16a66dfcf03b.JPG)


##### LINEAR JOINT CONTROL

Using the formula, q* = q0 + q we calculate the desired configuration(q*) of the robot on
Simulink.After solving Exercise 1, we manage to get the initial configuration of the robot. Now
we need to move it to a desired configuration.On Simulink, we add three blocks for calculating the
transformation matrix, velocity and center of mass. Hence, this will provide the torque commands
to reach the desired configuration.The blocks used are Joint Space Mass Matrix,Velocity Product
Torque and Matrix Multiply.
![Ex2Bd](https://user-images.githubusercontent.com/93926797/189100781-1f633587-39cf-4bc5-b3a3-932770371380.png)


__Without Gravity Compensation__

The robot will try to reach the desired position but will fail to do so because there is no gravity
compensation and it will act as zero torque demo robot once again.

##### LINEAR CARTESIAN CONTROL

Firstly, we need to determine the initial pose and orientation of the end-effector and we can get
this information from "Transformation matrix computation" and "Co-ordinate Transformation
conversion" blocks.The input is q from the robot model of the Ex-1 and then you save
the values of the Euler angles x y z and the "Trvec" pose x y z values.With this blocks, before
our PD controller we can get the desired pose of the end effector link.The input "EulZYX" is
the vector of the last three components of x* and the input "TrVec" is the vector of the first
three (where x* = x0 + x).
![ex3bd (2)](https://user-images.githubusercontent.com/93926797/189101036-d6a68a3a-e80e-4d7e-9a75-8ff793668f4a.png)


##### COMPUTED TORQUE CONTROL

We need to use the block of "polynomial trajectory" to get position,velocity and acceleration and
then need to proceed forward by connecting it to the clock.
If we remove the damping coefficient from each joint, then the shocks received at each joints are
minimized and the robot becomes robust and the robot works efficiently.

![ex4bd](https://user-images.githubusercontent.com/93926797/189101199-716aeecf-f29c-4989-ae7b-5386d717eda9.png)

__NOTE__ The results are attached with the report file.

__CONCLUSION__

The Universal Robots UR5, a highly flexible robotic arm enables safe automation of repetitive,
risky tasks.The UR5 is very easy to set up and program. This gives it one of the fastest payback
times on the market. This robot can be operational in less than half a day thanks to the simple
12
way of programming with a 3D visualisation.In the assignment, we analysed and compared the
parameters on different situations.Our entire work is based on analysis through graphs and reading
the outputs on Simulink.
