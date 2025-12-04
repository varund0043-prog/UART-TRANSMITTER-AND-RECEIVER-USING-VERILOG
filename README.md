UART VERILOG PROJECT - COMPLETE DOCUMENTATION
📌 PROJECT OVERVIEW
Complete UART communication system in Verilog

100MHz clock with 115200 baud rate configuration

Full-duplex serial communication implementation

Built-in loopback test capability

🎯 KEY FEATURES
Configurable clock frequency and baud rate

8-bit data + start bit + stop bit format

LSB-first transmission protocol

Triple synchronizer for metastability protection

Stop bit error detection

Modular design with separate TX/RX modules

🏗️ ARCHITECTURE
Top Module: uart.v (wrapper for TX and RX)

Transmitter: uart_tx.v (4-state FSM)

Receiver: uart_rx.v (4-state FSM with sync)

Testbench: uart_tb.v (comprehensive testing)

📊 SPECIFICATIONS
Clock: 100MHz

Baud: 115,200 bps

Bit period: 868 clock cycles

Sampling: Middle of bit (434 cycles)

Data format: 8N1 (8 data, no parity, 1 stop)

States: IDLE → START → DATA → STOP

🔧 TRANSMITTER (uart_tx.v)
4-state Finite State Machine (FSM)

Bit counter: 0 to 867 cycles per bit

LSB-first serial data output

Automatic start/stop bit generation

tx_done pulse signal after transmission

📡 RECEIVER (uart_rx.v)
Triple-stage synchronizer (rx_in → sync1 → sync2 → clean)

Middle-of-bit sampling (cycle 433)

Stop bit verification for error detection

rx_done pulse signal after reception

rx_error flag for invalid stop bits

🧪 TESTBENCH (uart_tb.v)
10 comprehensive test patterns:

0x00 - All zeros

0xFF - All ones

0x55 - 01010101

0xAA - 10101010

0xF0 - 11110000

0x0F - 00001111

0xA5 - 10100101

0x5A - 01011010

0x81 - 10000001

0x7E - 01111110

Loopback configuration (TX output → RX input)

Automatic pass/fail reporting

Success percentage calculation

Real-time signal monitoring

⚙️ TIMING DETAILS
Clock period: 10ns (100MHz)

Bit time: 8680ns (868 cycles × 10ns)

Baud calculation: 100MHz / 115200 ≈ 868 cycles

Half bit time: 434 cycles for sampling

Total transmission time: 10 bits × 8680ns = 86.8μs

🔄 STATE MACHINE DETAILS
Transmitter States:
IDLE: Wait for tx_start, output HIGH

START: Send start bit (LOW) for 868 cycles

DATA: Send 8 data bits (LSB first)

STOP: Send stop bit (HIGH) for 868 cycles

Receiver States:
IDLE: Wait for start bit (falling edge)

START: Verify start bit (LOW)

DATA: Sample 8 bits at middle points

STOP: Verify stop bit (HIGH), check error

📈 TEST RESULTS
10 test cases executed

Expected: 100% pass rate

Loopback verification of all patterns

Error-free stop bit detection

Proper synchronization verification



🚀 EDA PLAYGROUND STEPS
File Upload:

uart_tx.v (transmitter)

uart_rx.v (receiver)

uart.v (top module)

uart_tb.v (testbench)

Simulation Settings:

Simulator: Icarus Verilog

Language: Verilog

Top module: uart_tb

Timescale: 1ns/1ps

Run Simulation:

Compile all files

Execute simulation

View console output

Download waveforms (if needed)

✅ VERIFICATION CHECKS
All 10 test patterns pass

TX timing: 868 cycles per bit

RX sampling: at 434 cycles (middle)

Error detection works correctly

Synchronization prevents metastability

Reset functionality verified

🛠️ DESIGN HIGHLIGHTS
Robust input synchronization (3 stages)

Precise bit timing (counter-based)

Clean state machine transitions

Proper signal timing (setup/hold)

Comprehensive error checking

Modular and reusable code

📁 FILES SUMMARY
uart_tx.v: 80 lines - Transmitter logic

uart_rx.v: 95 lines - Receiver logic with fixes

uart.v: 25 lines - Top-level integration

uart_tb.v: 110 lines - Complete test suite

Total: ~310 lines of Verilog code

🎓 LEARNING OUTCOMES
UART protocol implementation

Finite State Machine design

Clock domain synchronization

Testbench development

Timing analysis and verification

Serial communication fundamentals
