# Traffic-Light-Controller-Using-Verilog-HDL
## Aim
To design and simulate a traffic light controller using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 simulation environment. The objective is to control the traffic lights for a junction with a specific time-based sequence for Red, Yellow, and Green lights.

## Apparatus Required
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.
FPGA board (optional for hardware verification).
Procedure
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Traffic Light Controller Verilog Code:

Write the Verilog code for the traffic light controller, using an FSM (Finite State Machine) to transition between Green, Yellow, and Red lights based on timing intervals.
Create the Testbench:

Write a testbench to simulate the traffic light controller. The testbench will check the sequence of light transitions based on time.
Add the Verilog Files:

Add the traffic light controller Verilog code and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado to verify the correct sequence of the traffic lights.
Observe the Waveforms:

Examine the waveform output to verify that the traffic light transitions through the Green, Yellow, and Red lights in the correct sequence.
Save and Document Results:

Capture screenshots of the waveform and save the simulation logs to include in your report.


### Verilog Code for Traffic Light Controller
```
module cyclic_lamp(clk,rst,light); 
input clk,rst; 
output reg [2:0] light; 
parameter [1:0]S0=2'b00,S1=2'b01,S2=2'b10; 
parameter RED=3'b100, GREEN=3'b010, YELLOW=3'b001; 
reg [1:0] state; 
always @(posedge clk) 
 case (state) 
 S0: begin // S0 means RED 
 light <= GREEN; state <= S1; 
 end 
 S1: begin // S1 means GREEN 
 light <= YELLOW; state <= S2; 
 end 
 S2: begin // S2 means YELLOW 
 light <= RED; state <= S0; 
 end
default: begin 
 light <= RED; 
 state <= S0; 
end 
endcase
endmodule
```
output

![trafficlight control](https://github.com/user-attachments/assets/0d7c8984-a917-442f-921a-67cafc47f696)

## Conclusion
In this experiment, a traffic light controller was successfully designed and simulated using Verilog HDL. The design controlled the traffic lights to switch between Green, Yellow, and Red in a cyclic manner based on timing intervals. The testbench verified that the traffic lights followed the correct sequence and timing. The simulation results confirm the correct functionality of the traffic light controller, demonstrating the effectiveness of Verilog HDL in designing FSM-based controllers for real-world applications.
