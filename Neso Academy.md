### STACK STRUCTURE

#### x86-64 Stack

%rsp

#### x86-64 Stack: Push

pushq Src

- Fetch operand at Src

- Decrement %rsp by 8

- Write operand at address given by %rsp

#### x86-64 Stack: Pop

popq Dest

- Read value at address given by %rsp

- Increment %rsp by 8

- Store value at Dest (must be register)

### CALLING CONVENTIONS

#### Procedure Control Flow

- Procedure call: call label

- Procedure return: ret

# Neso Academy

## Introduction

Sum - Carry

Architecture - Organization

Computer Architecture: 

- Functional Behaviour

- Design implementation

Computer Organization:

- Structural relationship

Functional Unit:

- Processor
  
  - Registers
  
  - Arithmetic Logic Unit
  
  - Timing & Control Unit
  
  - Interface

- Memory

- I/O Peripherals

Syllabus

- Basics classification

- Memory interfacing and hierarchy

- Computer organization

- I/O interfacing

- Instruction Pipelining

- Number system

## Basics

Instruction Set Architecture (ISA)

- Example:
  
  - MOV, ADD, STORE

Hardware Set Architecture (HSA)

- Example:
  
  - R1. R2. ADDER

History

- Charles Babbage

- Ada Lovelace

- Alan Turing

- Johann Von Neumann

## 

## Classification

Von Neumann Architecture (AKA Princeton Architecture)

![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-34-13-image.png)

Non- Von Neumann Architecture

- Harvard Architecture
  
  - ![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-35-10-image.png)

- Modified Harvard Architecture
  
  - ![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-35-20-image.png)

Computer Architecture / Flynn's Taxonomy

- SISD (Single Instruction stream, Single Data stream)
  
  - ![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-37-05-image.png)

- SIMD (Single Instruction stream, Multiple Data stream)
  
  - ![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-37-21-image.png)

- MISD (Multiple Instruction stream, Single Data stream)

- MIMD (Multiple Instruction stream, Multiple Data stream) / Multi Processor
  
  - ![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-10-37-39-image.png)

## 

## Introduction To Memory

Memory is the faculty of the brain which data or information is encoded, stored, and retrieved when needed.

**Time is essential.**

- Frequency: 2Ghz

- Time:
  
  - 1/Frequency.
  
  - 1/ 2 (10^9)
  
  - 1/2 * (10^-9) 
  
  - 1/2 nano seconds / task

Primary Memory

- Execution of instructions

- Dynamic RAM / DRAM

- Static RAM / SRAM (Cache)

Secondary Memory

- Storing Data

The Big Picture

- Processor -> Main Memory

- Processor -> Cache

- Main Memory -> Cache

- Main Memory -> Secondary Memory

## Memory Hierarchy

Hierarchy -> Ranking

MIPS = Million Instruction Per Second

## Question

Q1 Access Time

- T Cache = 30ns

- T MM = 150ns

- H Cache = 80%

- Tavg =
  
  - HCache*TCache + (1-HCache)(TMM)
  
  - 0.8*30ns + (1-0.8)(150ns)
  
  - 24ns + (0.2)(150ns)
  
  - 54ns

- Tavg2 = 
  
  - HCache*TCache+(1-HCache)(TCache+TMM)
  
  - 0.8*30ns + (1-0.8)(30ns+150ns)
  
  - 24ns + (0.2)(180ns)
  
  - 60ns

Q2 Access Time

- RR Miss = T Cache + T MM = 50ns

- RR Hit = T Cache = 5ns

- H Cache = 80%

- Tavg2 = 
  
  - HCache*TCache+(1-HCache)(TCache+TMM)
  
  - HCache*RRHit+(1-HCache)(RRMiss) 
  
  - 0.8*5ns + (1-0.8)(50ns)
  
  - 4ns + 10ns
  
  - 14ns

## Cache Memory

Cache Hit

Hit Latency

Tag Directory (Data Structure)

Cache Miss

Miss Latency

Page Fault

Page Hit

Page Fault Service Time

Locality of Reference

- Spatial Locality

- Temporal Locality

## Memory Mapping

![](C:\Users\asus\AppData\Roaming\marktext\images\2021-12-13-11-05-50-image.png)

Words = Smallest Addressable Unit of Memory

- Byte Addressable Memory:
  
  - 1 Word = 1 Byte

Example:

- Main Memory Size: 64 words

- Block Size: 4 Words

- No of Blocks in MM: 64/4 = 16
  
  - 0, 1, ..., 63

- Physical Address = Block Number + Block/Line Offset
  
  - Block Number
    
    - 2 log Blocks Size
    
    - 2 log 8 = 3 bits
    
    - 2 log 64 = 6 bits
  
  - Block / Line Offset
    
    - 2 log Words Size 

Example 2:

- Cache Size: 16 words

- Line Size: 4 Words

- No of Lines in Cache: 16/4 = 4
  
  - 0, 1, 2, 3

- Block Size =  Line Size

- Round Robin: 
  
  - Each Mapped Consecutively
  
  - Many to One
    
    - Least significant byte of MM Address == Cache Address
    
    - Most significant byte of MM Address == Cache Batch / Tag bits

## Question

Question 1:

- MM Size: 4GB

- Cache Size: 1 MB

- Block SIze: 4 KB

- Word Size: 1 Byte

- Question:
  
  - P.A. bits split?
  
  - Tag directory size?

- Solution:
  
  - MM Size: 4GB =
    
    - 4 * (2^30) Bytes
    
    - (2^2) * (2^30) Bytes
    
    - 2^32 Bytes
  
  - No of PA bits:
    
    - 2 log 2^32 = 32 bits
  
  - Block Size:
    
    - 4 * (2^10) Bytes
    
    - (2^2) * (2^10) Bytes
    
    - 2^12 Bytes
  
  - Block Offset:
    
    - 2 log 2^12 = 12 bits
  
  - No of Blocks in MM: 2^32 / 2^12 = 2^20
  
  - Block Number:
    
    - 2 log 2^20 = 20 bits
  
  - **PA bits split:**
    
    - 20 bits + 12 bits
  
  - Cache Size: 1MB = 1 * (2^20) Bytes
  
  - No of Lines in Cache = 2^20 / 2^12 = 2^8
  
  - Line Number:
    
    - 2 log 2^8 = 8 bits
  
  - **PA bits split:**
    
    - (20-8) bits + 8 bits + 12 bits
  
  - No of Tag bits:
    
    - PA bits - (line of btis + offset)
  
  - **PA bits split:**
    
    - Tag bits + line bits + offset bits
    
    - 12 bits + 8 bits + 12 bits
  
  - Tag directory size:
    
    - No of Lines in Cache = 2^8
    
    - No of Tag bits = 12
    
    - Tag directory size =
      
      - 2^8 * 12 bits
      
      - 3072 bits

Question 2:

- MM Size: 256 MB
  
  - (2^8) x (2^20) bits
  
  - 2^28 bits

- Cache Size: 512 KB
  
  - (2^9) x (2^10) bits
  
  - 2^19 bits

- No of Tag bits:
  
  - 2 log (MM Size / Cache Size)
  
  - 2 log (2^28 / 2^19)
  
  - 2 log 2^9
  
  - 9 bits

Question 3:

- MM Size: 16 GB
  
  - 2^4 x 2^30 bits
  
  - 2^34 bits

- No of PA bits:
  
  - 2 log 2^34
  
  - 34 bits

- Block Size: 16 KB
  
  - 2^4 x 2^10 bits
  
  - 2^14 bits

- Block Offset
  
  - 2 log 2^14
  
  - 14 bits

- Cache bits
  
  - PA bits - Tag bits - Offset bits
  
  - 34 bits - 10 bits - 14 bits
  
  - 10 bits

- No of Cache Lines = 2^10

- Line Size = Block Size = 2^14

- Cache Size
  
  - No of Cache Lines * Line Size
  
  - 2^10 * 2^14
  
  - 2^24 Bytes
  
  - 2^4 * 2^20 Bytes
  
  - 16 MB

## Another Questions

Question 1:

- Cache Size: 1 MB

- Block Size: 256 Bytes

- Word Size: 64 bits = 8 Bytes

- No of Words per Block
  
  - 256 / 8
  
  - 32

- T Cache: 3ns

- H Cache: 94%

- T MM:
  
  - 20 ns first
  
  - 5 ns rest

- Tavg2 =
  
  - 0.94*3ns + (1-0.94)(3ns + 20ns + (2^5-1)5ns)
  
  - 

PA bits 16 bit

2^2 * 2^4

B = 8bits

Tags = 4bits

4

64kb =

- 2^6 x 2^10

- 2^16

tsbb

Set 0: v1 tag0 blockM0-3

Set 1: v1 tag1 blockM12-15

1111 hit

0000 hit

miss

hit

hit

00

11

22

3

4

5
