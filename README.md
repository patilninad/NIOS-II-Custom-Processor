# > System on Chip(SoC) design with integrated NIOS-II Custom Soft-Core Processor Core Using Intel's Qsys System Design Tool:-    
The NIOS II embedded processor family is Altera's second-generation soft embedded processor solution. The NIOS II are 32-bit RISC processors that share a common instruction set architecture and are optimized for use in all of Altera's mainstream FPGA families. A Nios II processor system consists of a Nios II processor core, a set of on-chip peripherals, on-chip memory, and interfaces to off-chip memory, all implemented on a single Intel FPGA device.   
  # Features:-  
  1) Full 32-bit address space, data path and instruction set.  
  2) 32-bit general-purpose registers.   
  # NIOS II Processor System:-  
  ![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/NIOS%20II%20Processor%20System.PNG)  
  # NIOS II Processor Core Block Diagram:-
  ![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/NIOS%20II%20Processor%20Core%20Block%20Diagram.PNG)  
# > Intel Quartus Prime Development Suite:-    
  Intel's proprietary software to design for Intel FPGA's, System on Chip (SoCs), Complex Programmable Gate Arrays      (CPLDs) from design entry and synthesis to timing analysis,optimization, verification and simulation. Various components  of Quartus Prime are:  
  1) ModelSim - For simulating the design.  
  2) TimeQuest timing analyser - For analysing timing violations of the design and achieving timing closures.  
  3) Qsys - For system design.  
  4) Chip Planner - To view where the design is placed on the logic fabric by the compiler and to make changes if         required.    
  5) PowerPlay Power Analyser Tool - For analysing and achieving power requirements of the design.  
   # FPGA Design Flow:-  
  1) Design Entry: Schematic Capture, HDL, Importing IP blocks, State Machine Entry, Importing EDIF files.  
  2) Functional Simulation  
  3) Synthesis/Mapping   
  4) Place and Route  
  5) Timing Analysis   
  6) Simulation  
  7) Programming  
  8) Test and Integration  
  # > Arthmetic Logic Unit (ALU):-  
   # Schematic Diagram:-  
![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/ALU.PNG)   
   Intel Altera's MAX 10 FPGA Development Board family was the target device.      
   An 8x8 multiplier was designed. The result was stored in a 32x16 bit synchronous RAM. 8x8 multiplier and 32x16 bit RAM    was designed using Verilog HDL and converting the source code to a block diagram using quartus prime tools.  
   # RTL Viewer:-
![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/RTL%20viewer.PNG)  
   The main components are Multiply and Accumulate (MAC) block and RAM block.  
   # Technology Map Viewer (Post-Fitting):-  
  The block diagram was quite large to be fit into the snapshot.  
   # TimeQuest Timing Analyser:-  
   Performed timing closure for the pipelines multiplier by constraining all paths in the design and running the timing      analyser tool. Timing closure can be achieved by overcoming setup and hold time violation. Timing violation can lead to various errors such as:-    1) Hazards   2) Metastability  3) Race condition  4) Clock Skew  
   # ModelSim:-  
   ModelSim is a simulator from Mentor Graphics. The multiplier design was simulated by feeding various input test patterns. Following is the snapshot of the simulation window. 
   ![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/MentorGraphics.PNG)  
   # Pin Assignment:-  
   ![](https://github.com/patilninad/NIOS-II-Custom-Processor/blob/master/Pin%20Assignments.PNG)  
   There are different I/O standards. Such as single-ended and differential.  
   Single-ended I/O are faster but have poor noise immunity. Differential I/O are faster as well as have better noise immunity. But differential I/O consume twice the amount of pins then single-ended. Different input and output signals of the ALU were attached to different I/O banks of the FPGA. Here single-ended I/O +3.3V LVCMOS was used as default I/O standard.     
   # Intel(Altera) FPGA's configuration modes:-  
   1) JTAG - Uses USB-Blaster II cable to transfer the configuration data into the device config memory. This data is loaded onto the device on startup. Four types of ways in JTAG mode to configure the device:-  
   a) .sof(SRAM object file) - Transfers data directly onto the internal SRAM block.  
   b) .pof(programmable object file) - Transfers data onto the internal SRAM block via internal FLASH memory.   
   c) .jam/.jbc - ASCII file used by processors and test equipments to program devices via JTAG.  
   d) .jic(JTAG indirect configuration file) - is used to program EPCS(Altera serial configuration) devices.  
   2) Active Serial - A serial FLASH memory device stores the configuration image. The image is loaded onto the device on startup via serial interface.  
   4) Fast Passive Parallel - Uses a CPLD or a micro-processor to transfer the device configuration data from memory to FPGA device upon startup.  
