---
title: "Linux does not recognize my keyboard(tested ubuntu, Dreamlinux and Suse)"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2008-01-31
I´m trying to do a dualboot with vista and linux. The problem is, those distros listed do not recognize my keyboard(and I don´t want to test all distros just for this problem), every time I try to install one of those keyboard work at the first point :confused: (in ubuntu, the point where you can select install, check cd for defects and so on). My computer is new, and that may be one of the reasons. Its HP Pavilion m9066, here is detailed info from Cpu-Z:



CPU-Z 1.43 report file
Processor(s)	 
Number of processors	1
Number of cores	2 per processor
Number of threads	2 per processor
Name	AMD Athlon 64 X2 5000+
Code Name	Brisbane
Specification	AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
Package	Socket AM2 (940)
Family/Model/Stepping	F.B.1
Extended Family/Model	F.6B
Brand ID	4
Core Stepping	BH-G1
Technology	65 nm
Core Speed	2210.0 MHz
Multiplier x Bus speed	11.0 x 200.9 MHz
HT Link speed	1004.6 MHz
Stock frequency	2600 MHz
Instruction sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
L1 Data cache (per processor)	2 x 64 KBytes, 2-way set associative, 64-byte line size
L1 Instruction cache (per processor)	2 x 64 KBytes, 2-way set associative, 64-byte line size
L2 cache (per processor)	2 x 512 KBytes, 16-way set associative, 64-byte line size
Chipset & Memory	 
Northbridge	NVIDIA MCP61 rev. A3
Southbridge	NVIDIA MCP61 rev. A2
Graphic Interface	PCI-Express
PCI-E Link Width	x16
PCI-E Max Link Width	x16
Memory Type	DDR2
Memory Size	3072 MBytes
Memory Frequency	315.7 MHz (CPU/7)
CAS# Latency (tCL)	5.0 clocks
RAS# to CAS# (tRCD)	5 clocks
RAS# Precharge (tRP)	5 clocks
Cycle Time (tRAS)	15 clocks
Bank Cycle Time (tRC)	21 clocks
Command Rate (CR)	2T
System	 
System Manufacturer	HP-Pavilion
System Name	GU636AA-UUW m9066.sc
System S/N	CZH738094D
Mainboard Vendor	ASUSTek Computer INC.
Mainboard Model	NARRA2
BIOS Vendor	Phoenix Technologies, LTD
BIOS Version	5.11
BIOS Date	07/16/2007
Memory SPD	 
Module 1	DDR2, PC2-5300 (333 MHz), 512 MBytes, Hyundai Electronics
Module 2	DDR2, PC2-5300 (333 MHz), 512 MBytes, Hyundai Electronics
Module 3	DDR2, PC2-5300 (333 MHz), 1024 MBytes, Samsung
Module 4	DDR2, PC2-5300 (333 MHz), 1024 MBytes, Samsung
Software	 
Windows Version	Microsoft Windows Vista (6.0) Home Premium Edition (Build 6000)
DirectX Version	10.


My mouse is in usb port, and keyboard in keyboard port. When I first time installed everything, vista did not recognize my mouse untill I put it in the usb port, so I was thinking that maybe I need a usb keyboard? Or is there known solution that I just didn´t find?

---

### Post by LowSky on 2008-01-31
your using a PS/2 keyboard, not a usb keyboard with a PS/2Adapter?
 Is it a wireless keyboard, or a weird mutimedia one?
What brand keyboard (HP, logitech, microsoft?)
I just want you to clear that up for me.

I do find it odd that it works with the LIVECD and not with the a normal install.

Something tells me that you xorg.conf file may have something wrong with it, but not over 3 differnet versions of linux... thats just odd.

---

### Post by smurphy_it on 2008-01-31
It's probably your keyboard and there probably isn't much you can do about it.  I have had slow USB initializations on things like that in the past, and couldn't get anything done about it.  Usually a ROM chip on the keyboard which you can't hack.

---

### Post by jaytek13 on 2008-01-31
Just to throw this in here, I myself use a usb mouse and a PS/2 keyboard, and have never had any problems with that configuration, so that may not be your problem.

---

### Post by NorthernPaladin on 2008-01-31
Its a PS/2 keyboard, and it does not work with the live-cd. As I said, it only works at the very first point, where you can select install, install in safe mode, check cd for defects etc. After I select anything in that menu, it does not work anymore. Even if I press numlock or capslock, nothing happens( the light does not go off or on).

---

### Post by NorthernPaladin on 2008-02-01
Bump! I really need help with this one

---

### Post by smurphy_it on 2008-02-04
Try another keyboard for argument sake.

---

### Post by smurphy_it on 2008-03-07
Try the ubuntu alternate CD ?  Available [URL="http://releases.ubuntu.com/gutsy/"]here.
[/URL]

---

