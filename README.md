# UCAS Computer Organization and Design Labs

Course labs covering custom CPU, cache, DMA, and accelerator design. Each project pairs runnable RTL/software with a detailed LaTeX report under `reports/`.

## Repo Layout
- `reports/`: Lab reports (`prj1.tex` … `prj5.4.tex`) that document design choices, waveforms, and performance results.
- `alu_rf/`: Basic building blocks (lab 1) – register file (`reg_file.v`) and ALU (`alu.v`).
- `simpleCPU/`: Simple MIPS-like CPU (lab 2) with barrel shifter (`shifter.v`) and core (`simple_cpu.v`).
- `customCPU_MIPS/`: Custom multicycle MIPS CPU (lab 3) with real memory/I/O handshakes and perf counters (`custom_cpu_mips.v`).
- `customCPU_RISCV/`: Custom multicycle RISC-V CPU (lab 4) with revised decode/PC update and ALU/shift op recoding (`custom_cpu_riscv.v`, `alu_riscv.v`).
- `cache/`: I-cache and D-cache RTL (lab 5.2) – 4-way set-associative, pseudo-LRU, write-back/write-allocate (`icache.v`, `dcache.v`, arrays/ways).
- `dnn/`: Lab 5.3 assets – Booth multiplier (`mul.v`), RISC-V CPU with MUL support (`custom_cpu_riscv_withmul.v`), convolution/pooling software (`conv.c`), Verilator testbench (`tb_mul.cpp`), `Makefile`.
- `dma/`: Lab 5.4 assets – DMA engine core (`engine_core.v`), MIPS CPU with DMA/interrupt support (`custom_cpu_MIPS_withDMA.v`), data mover app (`data_mover.c`), interrupt handler (`intr_handler.S`).
- `journal.md`: Personal notes/log (if needed alongside reports).

## Project Highlights (see reports for full details)
- Lab 1 (`reports/prj1.tex`, `alu_rf/`): Synchronous-write/async-read register file with x0 hardwired to zero; gate-level ALU (no behavioral always) handling signed/unsigned add/sub, logic, shifts, flags.
- Lab 2 (`reports/prj2.tex`, `simpleCPU/`): Single-cycle style MIPS core covering ~45 instructions; modular decode by instruction format, PC update logic with mutually exclusive enables, and optimized byte/word store handling.
- Lab 3 (`reports/prj3.tex`, `customCPU_MIPS/`): One-hot FSM multicycle MIPS CPU with external memory, UART driver (puts), and perf counters tracking CPI/memory stalls/branches.
- Lab 4 (`reports/prj4.tex`, `customCPU_RISCV/`): RISC-V multicycle CPU highlighting PC pipeline differences vs. MIPS (snpc/bnpc/dnpc split), recoded ALU/shift ops, and decode refactor per opcode/funct fields.
- Lab 5.2 (`reports/prj5.2.tex`, `cache/`): 4-way set-associative I/D caches; pseudo-LRU via binary-tree bits, burst refill/write-back, bypass path handling, and microbench/turbo_eval performance gains.
- Lab 5.3 (`reports/prj5.3.tex`, `dnn/`): Booth multiplier integrated into CPU MUL state, fixed-point convolution/pooling kernels, GPIO-based accelerator hook, and performance counter comparisons (software vs. MUL vs. accelerator).
- Lab 5.4 (`reports/prj5.4.tex`, `dma/`): DMA engine with dual read/write FSMs, burst length/count control, FIFO bridging, interrupt generation/ack; CPU interrupt path with EPC save/ERET restore and mask logic, plus DMA-aware ISR.