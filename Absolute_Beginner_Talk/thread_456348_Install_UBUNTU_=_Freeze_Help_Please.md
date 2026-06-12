---
title: "Install UBUNTU = Freeze Help Please"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Leandroaguirre on 2007-05-27
My English is very poor. So... I will be synthetic

Try one: Install from live CD... Result: Freeze while installing (5 seconds after first UBUNTU selection screen)

Try two: Install from Alternate CD: Result: Install OK. Partition OK. Put new user OK. FInish instalation. Then Reboot and... freeze!!!

I look into /var/log register and there is nothing relevant. (I use a disk browser from WinXP)

May You help?

**Motherboard Information**
	
Motherboard Model		DG965WH
Motherboard Vendor		Intel Corporation
Motherboard Version		AAD41692-304

**Processor**
	
	Model		Intel Pentium (6x86)
	Type		Primary Processor
	Vendor		Intel Corporation
	Family		6th Generation of Intel Processors
	Hardcoded Name		Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz
	Frequency		1864 MHz
	Family/Model/Stepping		6/15/6
	Logical CPU Count		2
	CL Flush		8
 			
***	Detailed Info***
	
	Address Bus Width		36 Bit
	Core Details		20 Entry RS, 40 Entry ROB
	Data Bus Width		64 Bit, Separate 64 Bit Backside L2 Cache Bus
	Execution Speed		Up to 5 µOPs/Cycle
	Execution Units		2x ALU, Load, Store Address, Store Data, Pipelined FPU
	First Introduction		Novembre 1st, 1995
	Floating Point		Integrated
	I/O Voltage		3.3 v
	Instruction Decoder		3x IA-32/Cycle, 6x µOPs/Cycle
	Instruction Set		IA-32
	Multimedia		N/A
	Multiprocessing		SMP, 4 Processors, using integrated local APICs
	Physical Memory		2^36 Bit (64 GB)
	Pipeline Depth		12 (In-order) plus 2 (Out-of-order) Stages
	Power Management		HLT, STPCLK, SMI/SMM
	Processor Core		RISC, Out-of-order and Speculative Execution
	Processor Modes		Real, Protected, Virtual, Paging, SMM, Probe Mode
	Registers		32-bit Integer, 80-bit FP, 40 Entry RAT
	Split Voltage		Yes (Automatically determined via VID Pins)
	Virtual Memory		65,528 GB (~64 TB)


**RAM 1Gb**

**Hard Disk**
	**ATA Information**
	
	Controller		Tertiary Controller
	Position		Master Drive
	Model Number		WDC WD2500KS-00MJB0
	Firmware Revision		02.01C03
	Serial Number		WD-WCANK6636860
	Supported ATA Standard		ATA-1, ATA-2, ATA-3, ATA-4, ATA-5, ATA-6, ATA-7
 			
	Configuration
	
	Interface		ATA
	Media Type		Fixed Media
	CHS Geometry		16383 / 16 / 63
	Current Translation CHS Geometry		16383 / 16 / 63
	Current Translation Total Sectors		16,514,064 Sectors
	LBA Total Sectors		268,435,455 Sectors
	48-Bit LBA Total Sectors		488,397,168 Sectors
	Has Multiple Logical Sectors Per Physical Sector		No
	Logical Sector Longer Than 512 Bytes		No
	Buffer Size		32768 Sectors (16.00 MB)
	Sector Type		Hard-sectored
	Disk Transfer Rate		5-10 Mbit/Sec
	Number of ECC Bytes		50
	Maximum Sectors Per Interrupt		16 Sectors

---

### Post by Leandroaguirre on 2007-05-27
where can I find some help?

---

### Post by Immolatus on 2007-05-27
I'm assuming you've installed the latest version (7.04 feisty). 
Maybe try 6.10 edgy or 6.06 LTS for the sake of the dual core.
Or to shake out any other hardware issues .

---

### Post by Pollywoggy on 2007-05-27
When your machine freezes, can you get a console?

What I mean is this.  Let the machine finish booting, let it freeze.  Then do ctrl-alt-F2
When you do that, do you get a login prompt?

---

