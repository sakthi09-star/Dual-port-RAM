# Dual-port-RAM
Dual-port RAM in Verilog with parameterized width and depth. Supports synchronous read and write using separate addresses and enable signals. Includes active-high reset and a testbench with waveform generation for simulation using Icarus Verilog and GTKWave.

# Dual Port RAM (Verilog)

## Overview
This project implements a simple synchronous Dual-Port RAM using Verilog HDL. It supports independent read and write operations using separate addresses and enable signals. This is a basic RTL memory design useful for FPGA/ASIC learning.

## Features
- Parameterized RAM (width, depth, address size)
- Synchronous read and write
- Active-high reset (clears memory)
- Separate read/write ports
- Testbench with waveform generation (VCD)

## Design Parameters
- RAM_WIDTH = 8 bits  
- RAM_DEPTH = 256 locations  
- ADDR_SIZE = 8 bits  

## Ports

### Inputs
- clk : Clock signal  
- rst : Reset signal (active high)  
- data_in : Data input  
- wr_addr : Write address  
- rd_addr : Read address  
- wr_en : Write enable  
- rd_en : Read enable  

### Output
- data_out : Data read from memory  

## Working
- On reset: memory cleared and output set to 0  
- On clock edge:
  - If wr_en = 1 → data is written to wr_addr  
  - If rd_en = 1 → data is read from rd_addr  

## Testbench
- Clock period = 10ns  
- Reset applied at start  
- Two write operations performed  
- One read operation performed  
- Uses $monitor for live output  
- Generates dump.vcd for GTKWave  

## Simulation (Icarus Verilog)

### Compile
iverilog -o sim dual_ram.v dual_ram_tb.v

### Run
vvp sim

### Waveform
gtkwave dump.vcd

## Example Output
time=0, data_in=00, wr_en=0, wr_addr=00, rd_en=0, rd_addr=00, data_out=00  
time=10, data_in=FF, wr_en=1, wr_addr=1A  
time=20, data_in=0F, wr_en=1, wr_addr=42  
time=40, rd_en=1, rd_addr=42, data_out=0F  

## Applications
- FPGA memory blocks  
- Cache modeling  
- Digital design practice  
- RTL simulation learning  

## Author
Verilog RTL learning project focused on memory design and simulation flow.
