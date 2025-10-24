# simulink-rocket-simulator
This MATLAB-Simulink project helps simulate a rocket. It plots velocity, altitude, angle, thrust, drag, and net force. 

# Requirements
MATLAB, Simulink, Aerospace Toolbox and Blockset
Thrust curve of the rocket motor in .csv format. Time is the first column; thrust in Newtons is the second.

# Usage
1. Open the model file in Simulink.

2. The inputs of the program are on the right side of the model.

3. Import the thrust curve into "Import Thrust curve"

4. To change Wind speed, go into the "Wind" block and set the "Final Value" to the wind speed in miles per hour (mph).

5. Enter the ground level above sea level (ASL) into "Ground level (m)". This only affects the air density calculations

6. Enter mass in kilograms (kg) into "Mass (kg)"

7. Enter the surface area from the top of the rocket in meters squared (m^2) into "Surface Area (m^2)"

8. Enter the drag coefficient into "Drag Coeff.". 
    a.  If you don't know it, keep 0.6 as a baseline.
    b.  Launch the rocket in real life, and simulate that launch with this model.
    c.  Try to get the simulated apogee as close as possible to the actual apogee. Increasing the Coefficient of Drag decreases the apogee, and vice versa.
    d.  You now have a more accurate Drag Coefficient.

# Output Analysis
Double click the "Graph all (ft)" block. This graphs Velocity, Altitude, and zero against time.

Find the point where velocity = 0; this is the time of apogee. For better apogee height, set your motor ejection delay to fire the ejection charge after apogee.

Everything after that apogee point is inaccurate since the rocket is in free fall. The drag is also in the wrong direction when the velocity is negative.

# What this Models
- The thrust curve of the rocket
- Wind and its effect on the rocket's angle
- How the rocket's angle reduces the upwards pointing thrust
- Real time drag
- The air density at the rocket's height and how it affects the drag.

# Improvements to be Made
- Mass reducing in flight
- Implementing a parachute model
- Fixing Drag direction for negative velocities
- General usability (putting Thrust, Drag, and total force scopes in the correct area)
- Temperature effects
- Horizontal motion
- Modeling the angle as changing because of a force, not as the arctan of wind speed divided by velocity.

# Mix of Units
The units in the IO area are mixed because of what I used it for (American Rocketry Challenge).
You can change them by, take the wind speed for example, changing the input unit of the "Wind Speed (m/s)" block from "mph" to "m/s".

# Why I Made This
In my second year competing in the American Rocketry Challenge, I was curious to know how OpenRocket simulates rockets, which is what my team and I used to design and simulate our rockets. I also wanted a simulator in which I knew everything that it modeled, unlike in Open Rocket, in which, without reviewing the source code, I know very little about its physics and what it does and doesn't model. Using Simulink helps with this too, since one I see what factors of a rocket's flight it models. 