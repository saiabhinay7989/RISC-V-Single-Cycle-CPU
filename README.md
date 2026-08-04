# RISC-V Single Cycle CPU

A Verilog implementation of a **32-bit Single-Cycle RISC-V Processor** supporting the **RV32I Base Integer Instruction Set**. The processor executes each instruction in a single clock cycle and implements the complete datapath and control logic required for instruction fetch, decode, execute, memory access, and write-back.

---

## Overview

This project implements a single-cycle RISC-V CPU following the RV32I ISA. Every instruction is completed in one clock cycle without pipelining, making it suitable for understanding processor architecture and datapath design.

The processor includes:

- Program Counter (PC)
- Instruction Memory
- Register File
- Immediate Generator
- ALU
- Branch Comparator
- Data Memory
- Control Unit
- PC Selection Logic

---

## Supported RV32I Instructions

### R-Type
- ADD
- SUB
- SLL
- SLT
- SLTU
- XOR
- SRL
- SRA
- OR
- AND

### I-Type
- ADDI
- SLTI
- SLTIU
- XORI
- ORI
- ANDI
- SLLI
- SRLI
- SRAI
- LW
- JALR

### S-Type
- SW

### B-Type
- BEQ
- BNE
- BLT
- BGE
- BLTU
- BGEU

### U-Type
- LUI
- AUIPC

### J-Type
- JAL

---

# Processor Architecture

The processor follows the standard single-cycle datapath.

```
                +----------------------+
                | Program Counter (PC) |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Instruction Memory   |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Control Unit         |
                +----------+-----------+
                           |
      +--------------------+--------------------+
      |                                         |
      v                                         v
+-------------+                         +----------------+
| Register    |                         | Immediate Gen  |
| File        |                         +----------------+
+------+------+                                  |
       |                                          |
       +------------+-----------------------------+
                    |
                    v
               +---------+
               |   ALU   |
               +----+----+
                    |
          +---------+----------+
          |                    |
          v                    v
   Data Memory          Branch Comparator
          |
          v
     Write Back
          |
          v
     Register File
```

---

# Project Modules

| Module | Description |
|---------|-------------|
| Program Counter | Stores the current instruction address |
| Instruction Memory | Fetches instructions using the PC |
| Register File | 32 × 32-bit general-purpose registers |
| Immediate Generator | Generates immediates for I, S, B, U and J formats |
| ALU | Performs arithmetic and logical operations |
| Branch Comparator | Performs branch comparisons |
| Control Unit | Generates datapath control signals |
| Data Memory | Handles load/store operations |

---

# Features

- RV32I Base ISA implementation
- Single-cycle execution
- Separate Instruction and Data Memory
- Modular Verilog design
- Parameterized datapath modules
- Branch and jump support
- Load and Store instructions
- Simulation ready using Vivado

---

# Verification

The processor was verified using custom RISC-V assembly programs covering:

- Arithmetic instructions
- Logical instructions
- Shift operations
- Immediate instructions
- Load and Store operations
- Branch instructions
- Jump instructions

Simulation waveforms confirmed correct datapath operation and instruction execution.

---

# Results

- Successfully implemented a complete **RV32I Single-Cycle CPU** in Verilog.
- Verified execution of arithmetic, logical, memory, branch and jump instructions using custom test programs.
- Demonstrated correct interaction between datapath modules including ALU, Register File, Control Unit, Data Memory and Program Counter.

---

# Tools Used

- Verilog HDL
- Xilinx Vivado
- RISC-V RV32I ISA

---

# Repository Structure

```
.
├── top.v
├── control_unit.v
├── alu_logic.v
├── reg_file.v
├── program_counter.v
├── inst_mem.v
├── data_mem.v
├── imm_gen.v
├── branch_comp.v
├── instructions.mem
└── data_mem.mem
```

---

# Future Improvements

- Five-stage pipelined processor
- Hazard Detection Unit
- Data Forwarding Unit
- Branch Prediction
- CSR Instructions
- Interrupt Support

---

# Author

Sai Abhinay R
