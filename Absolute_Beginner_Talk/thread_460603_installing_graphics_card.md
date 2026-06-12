---
title: "installing graphics card"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-31
ok i'm trying to install a intel media accerator/ graphics card this what the dianogsitcs report said from my xp so u guys know what i need...
> 	Intel(R) Graphics Media Accelerator Driver Report


Report Date:		05/29/2007
Report Time[hr:mm:ss]:	19:29:18
Driver Version:		6.14.10.4764
Operating System:		Windows XP* Home Edition, Service Pack 2 (5.1.2600)
Default Language:		English
DirectX* Version:		9.0
Physical Memory:		501 MB
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	128 MB
Graphics Memory in Use:	9 MB
Processor:		x86
Processor Speed:		3333 MHZ
Vendor ID:		8086
Device ID:		2582
Device Revision:		04


*   Accelerator Information   *

Accelerator in Use:		Intel(R) 82915G/GV/910GL Express Chipset Family
Video BIOS:		1295
Current Graphics Mode:	1024 by 768 True Color (60 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Monitors: 1


*   Monitor   *

Monitor Name:		Plug and Play Monitor
Display Type:		Analog
Gamma Value:		2.29
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: 11.0  inches
			Vertical:   9.0  inches
Monitor Supported Modes:
640 by 480 (60 Hz)
640 by 480 (67 Hz)
640 by 480 (72 Hz)
640 by 480 (75 Hz)
720 by 400 (70 Hz)
800 by 600 (56 Hz)
800 by 600 (60 Hz)
800 by 600 (72 Hz)
800 by 600 (75 Hz)
832 by 624 (75 Hz)
1024 by 768 (60 Hz)
1024 by 768 (70 Hz)
1024 by 768 (75 Hz)
Display Power Management Support:
	Standby Mode:	Not Supported
	Suspend Mode:	Not Supported
	Active Off Mode: Supported

* Other names and brands are the property of their respective owners.                                                                                                                                                                                               

then on another thread a kid said i needed to type "lspci -v | less", then scroll down until you find something relating to graphics... and i did and this is what i got ..... > 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller
 Hub (rev 04)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated 
Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 30200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ffe0 [size=8]
        Memory at 20000000 (32-bit, prefetchable) [size=256M]
        Memory at 30280000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 302c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

now what do i do and if i could i would like to install that hd audio or does this mean there installed?

---

### Post by baskettplayr on 2007-05-31
someone plz help!!!!

---

### Post by baskettplayr on 2007-05-31
bump

---

### Post by kernel tom on 2007-05-31
the drivers for ur card should be in the following package

sudo apt-get install xorg-xserver-video-intel

i'm not 100% sure but that might do it

---

### Post by baskettplayr on 2007-05-31
this is what it said > kodey@kodey:~$ sudo apt-get install xorg-xserver-video-intel
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-xserver-video-intel
kodey@kodey:~$ 




---

### Post by baskettplayr on 2007-05-31
go here instead [http://ubuntuforums.org/showthread.php?t=460685]("http://ubuntuforums.org/showthread.php?t=460685")

---

### Post by kernel tom on 2007-05-31
crap...
my mistake 

try 

sudo apt-get install xserver-xorg-video-intel

---

