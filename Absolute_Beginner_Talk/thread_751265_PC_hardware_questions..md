---
title: "PC hardware questions."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2008-04-10
PC hardware questions.

have mostly been a Mac guy all my life, but recently have been using linux a lot on a new PC.

My wife has a Dell Precision 530 currently running Windows XP, which is rather draggy.

I would like to upgrade the hardware (RAM & hard drive) and install ubuntu.

I have no idea how to :

1 - figure out how much RAM it currently has
figure out how much RAM I can put in
what kind should I buy
and where I can buy it...

the same goes for the hard drive...

2 - I think it uses EIDE (not SATA) but am not sure
I don't know how much capacity it can go up to (that may be set by the OS, I guess.)
where I can get those drives? - I wonder if anybody still makes EIDE drives, or if I should look for used ones (possibly NOT a good idea)

I think I can find manuals online that tell me how to open the case and change the drives & RAM...

hopefully it makes sense to do this, rather than just buy a new PC - I've seen them for $400 with 2 GB RAM installed...

thanks for any input,


W

---

### Post by Inxsible on 2008-04-10
You can simply right click on My computer on the desktop and then select Properties. The General tab will show you the amount of memory it currently has.

As for the type, you will need to open the tower and remove a memory module and check the make/model etc.

---

### Post by amazingtaters on 2008-04-10
Dell should also provide specs for it's computers. You may have to dig but they're there. I used to have an old Dell Dimension 2800 circa 2000, and a few years later wanted to upgrade the RAM. Looked online and found that Dell had put RDRAM in the box, which is majorly expensive and hard to find. Of course, Dell would sell me a Gig of the stuff for around 300 bucks. Ended up building a new compy. As far the hdd goes, it should be easy to tell whether it is IDE or SATA. Take the case off, and the if there is a cable connecting it to and IDE port on the mobo then its IDE. The IDE connector is much bigger than a SATA connector.

---

### Post by arpinology on 2008-04-10
an easier, less intrusive way to determing what type of ram module you have is to goto [http://www.crucial.com](http://www.crucial.com).  

you have two options there.  you can install a program which will give you a full system info printout or you can choose your make/model of your commercially manufactured laptop and their database will provideyou with compatible modules.  

just copy down what kind they offer you, then gotoanother website and search around for the best price.  

you dont have to purchase anything from crucial...just exploit their helpfulness.

---

### Post by amazingtaters on 2008-04-10
> **arpinology said:**
> an easier, less intrusive way to determing what type of ram module you have is to goto [http://www.crucial.com](http://www.crucial.com).  

you have two options there.  you can install a program which will give you a full system info printout or you can choose your make/model of your commercially manufactured laptop and their database will provideyou with compatible modules.  

just copy down what kind they offer you, then gotoanother website and search around for the best price.  

you dont have to purchase anything from crucial...just exploit their helpfulness.

Wow that's a really excellent idea. I had no idea Crucial did that.

---

### Post by Daveg4otu on 2008-04-10
RAM and HDDs are easy enough to install.... check Dell site for specs bit it will almost certainly be  an IDE HDD.


Regarding  Drive capacity - on the Dell site - if you can locate the  Motherboard  make/model ...check at the manufacturers website for any BIOS flashes - it *may * be neccessary if you want to upgrade to a very large HDD (250 GB etc)

---

### Post by Therion on 2008-04-10
You can go to [www.newegg.com](www.newegg.com) and use their memory module locator for you.  However I've used a LOT of Crucial memory and recommend it highly.  Their prices are usually VERY hard to beat as well.

If you want to know all the gory details about your PC, I can suggest you go to Start/Run and in the little text-box type in: **dxdiag** [enter].

Click on "Save All Information to a File" and it will create a little .txt file on your desktop.  Copy and paste the contents of that file (the whole thing) into a new post in this thread.  

And don't worry, there's nothing confidential or compromising in the least in the whole of that report.  It's just a detailed report on the hardware profile.

---

### Post by aeiah on 2008-04-10
[IDE hard drive and cable](http://www.nuggetlab.com/comptia_files/equipment/hd_Close-up%20of%20IDE%20drive%20and%20ribbon%20cable.jpg)

[sata hard drive and cable](http://lib.store.yahoo.net/lib/cooldrives/ultraflex-sata-cable-1.jpg)

---

### Post by willfriedwald on 2008-04-10
thanks for all the amazing feedback!

I went to crucial - maybe I did something wrong, but it seems that 512 of memory for the Dell P 530 was $269 each - meaning it's over $500 for just one gig?  doesn't seem worth it, when one can get a new tower with more RAM in it pre-installed.

CT592108 512MB, 184-pin RIMM (x2)
shop for morePrecision WorkStation 530  upgrades

will check out new egg.... excuse me, newegg!

will run diagnostics & specs when I get back home tonight...

thanks again!

w

---

### Post by linux phreak on 2008-04-10
Hi you can download a small program called CPU-Z .Just google for it.It does not need installation.It will display all the computer details.

---

### Post by Therion on 2008-04-10
Oh boy... You may be in for a nasty shock.  The Dell Precision desktops use PC800 RDRAM.  Also known as RAMBUS.
You'd be better off, most likely, replacing the PC.  The memory price you were quoted is not out of line for that memory type.  

So, yes, in short, 1GB of memory for that PC is going to set you back $500.00 or thereabouts.

---

### Post by willfriedwald on 2008-04-11
when you're right, you're right!

I ran CPU-Z - fortunately, I figured out that it has a text export thing so that I don't have to retype the info.

will put the whole thing below (if anybody cares) but this is what seems to be pertinent re RAM:

Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		RDRAM
Module format		RIMM
Manufacturer (ID)	Samsung (CE59414730303030)
Size			128 MBytes
Max bandwidth		PC800-45 (400 MHz)
Part number		MR16R 1624AF0-CK8
Serial number		23EA6802
Manufacturing date	Week 03/Year 02

Attributes
Data width		16 bits
EPP			no
XMP			no

DIMM #2

General
Memory type		RDRAM
Module format		RIMM
Manufacturer (ID)	Samsung (CE59414730303030)
Size			128 MBytes
Max bandwidth		PC800-45 (400 MHz)
Part number		MR16R 1624AF0-CK8
Serial number		23516802
Manufacturing date	Week 03/Year 02

Attributes
Data width		16 bits
EPP			no
XMP			no

-----

so....

2 x 128

256 K altogether! No wonder this thing freezes every 20 seconds.

I gather that there's no reasonably economical way even to get half a gig of RAM onto this? 

next question: if I leave it as it is now, with only 256 k total memory, does it make sense to install ubuntu?  I'm thinking U will still do a better job than windows.  or am I wrong?

w


------------

full results below....

---

### Post by willfriedwald on 2008-04-11
here are those full results from cpu-z (feel free to skip!) :

-------------------------
  CPU-Z version 1.44.2
-------------------------

Processors Map
------------------------------------------------------------------------------------

Number of processors	2
Number of threads	2

Processor 0
    -- Core 0
        -- Thread 0
Processor 1
    -- Core 0
        -- Thread 0


Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		1 (max 1)
Number of threads	1 (max 1)
Name			Intel Xeon
Codename		Foster
Specification		Intel(R) Xeon(TM) CPU 1.50GHz
Package			Socket 603 mPGA (platform ID = 1h)
CPUID			F.1.2
Extended CPUID		F.1
Brand ID		14
Core Stepping		D0
Technology		0.18 um
Core Speed		1495.5 MHz (15.0 x 99.7 MHz)
Rated Bus speed		398.8 MHz
Stock frequency		1500 MHz
Instructions sets	MMX, SSE, SSE2
L1 Data cache		8 KBytes, 4-way set associative, 64-byte line size
Trace cache		12 Kuops, 8-way set associative
L2 cache		256 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		no
Features		

Processor 2 (ID = 6)
Number of cores		1 (max 1)
Number of threads	1 (max 1)
Name			Intel Xeon
Codename		Foster
Specification		Intel(R) Xeon(TM) CPU 1.50GHz
Package			Socket 603 mPGA (platform ID = 1h)
CPUID			F.1.2
Extended CPUID		F.1
Brand ID		14
Core Stepping		D0
Technology		0.18 um
Core Speed		1495.5 MHz (15.0 x 99.7 MHz)
Rated Bus speed		398.8 MHz
Stock frequency		1500 MHz
Instructions sets	MMX, SSE, SSE2
L1 Data cache		8 KBytes, 4-way set associative, 64-byte line size
Trace cache		12 Kuops, 8-way set associative
L2 cache		256 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		no
Features		


Thread dumps
------------------------------------------------------------------------------------

CPU Thread 0
APIC ID			0
Topology		Processor ID 0, Core ID 0, Thread ID 0
Type			01001007h
Max CPUID level		00000002h
Max CPUID ext. level	80000004h

Function		eax		ebx		ecx		edx
0x00000000		0x00000002	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F12	0x0001080E	0x00000000	0x3FEBFBFF
0x00000002		0x665B5001	0x00000000	0x00000000	0x007A7040
0x80000000		0x80000004	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000000	0x00000000
0x80000002		0x20202020	0x20202020	0x20202020	0x20202020
0x80000003		0x6E492020	0x286C6574	0x58202952	0x286E6F65
0x80000004		0x20294D54	0x20555043	0x30352E31	0x007A4847

Cache descriptor	Level 1 D	8 KB	1 threads	
Cache descriptor	Level 1 T	12 KB	1 threads	
Cache descriptor	Level 2 U	256 KB	1 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00900
MSR 0x00000017		edx = 0x00040000	eax = 0x00000000
MSR 0x0000002A		edx = 0x00000000	eax = 0x00000F02
MSR 0x000001A0		edx = 0x00000000	eax = 0x00000089

CPU Thread 1
APIC ID			6
Topology		Processor ID 6, Core ID 0, Thread ID 0
Type			01001007h
Max CPUID level		00000002h
Max CPUID ext. level	80000004h

Function		eax		ebx		ecx		edx
0x00000000		0x00000002	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F12	0x0601080E	0x00000000	0x3FEBFBFF
0x00000002		0x665B5001	0x00000000	0x00000000	0x007A7040
0x80000000		0x80000004	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000000	0x00000000
0x80000002		0x20202020	0x20202020	0x20202020	0x20202020
0x80000003		0x6E492020	0x286C6574	0x58202952	0x286E6F65
0x80000004		0x20294D54	0x20555043	0x30352E31	0x007A4847

Cache descriptor	Level 1 D	8 KB	1 threads	
Cache descriptor	Level 1 T	12 KB	1 threads	
Cache descriptor	Level 2 U	256 KB	1 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00800
MSR 0x00000017		edx = 0x00040000	eax = 0x00000000
MSR 0x0000002A		edx = 0x00000000	eax = 0x00003F02
MSR 0x000001A0		edx = 0x00000000	eax = 0x00000089


Chipset
------------------------------------------------------------------------------

Northbridge		Intel i860 rev. A3
Southbridge		Intel 82801BA (ICH2) rev. 04
Graphic Interface	AGP
AGP Revision		2.0
AGP Transfer Rate	4x
AGP SBA			supported, enabled
Memory Type		RDRAM
Memory Size		256 MBytes
Channels		Dual
Memory Frequency	398.8 MHz (1:1)
Total CAS# (tRDRAM)	9
Row To Column (tRCD)	9


Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		RDRAM
Module format		RIMM
Manufacturer (ID)	Samsung (CE59414730303030)
Size			128 MBytes
Max bandwidth		PC800-45 (400 MHz)
Part number		MR16R 1624AF0-CK8
Serial number		23EA6802
Manufacturing date	Week 03/Year 02

Attributes
Data width		16 bits
EPP			no
XMP			no

DIMM #2

General
Memory type		RDRAM
Module format		RIMM
Manufacturer (ID)	Samsung (CE59414730303030)
Size			128 MBytes
Max bandwidth		PC800-45 (400 MHz)
Part number		MR16R 1624AF0-CK8
Serial number		23516802
Manufacturing date	Week 03/Year 02

Attributes
Data width		16 bits
EPP			no
XMP			no

Dump Module #1
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   02 08 01 01 97 C5 05 20 02 05 08 14 0A 08 08 13 
10   1E 59 AA 00 00 00 00 00 00 00 00 00 00 00 00 04 
20   8D 32 28 11 05 90 00 64 64 96 40 0A 66 55 5D 00 
30   00 00 01 90 24 9C 50 3C 4D 28 1E 2A 20 00 00 09 
40   CE 59 41 47 30 30 30 30 01 4D 52 31 36 52 20 31 
50   36 32 34 41 46 30 2D 43 4B 38 00 30 41 02 03 23 
60   EA 68 02 04 10 0F 00 00 00 10 52 00 00 00 00 00 
70   00 00 00 00 30 31 32 42 52 00 00 00 00 00 00 AC 
80   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
90   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
A0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Dump Module #2
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   02 08 01 01 97 C5 05 20 02 05 08 14 0A 08 08 13 
10   1E 59 AA 00 00 00 00 00 00 00 00 00 00 00 00 04 
20   8D 32 28 11 05 90 00 64 64 96 40 0A 66 55 5D 00 
30   00 00 01 90 24 9C 50 3C 4D 28 1E 2A 20 00 00 09 
40   CE 59 41 47 30 30 30 30 01 4D 52 31 36 52 20 31 
50   36 32 34 41 46 30 2D 43 4B 38 00 30 41 02 03 23 
60   51 68 02 04 10 0F 00 00 00 10 52 00 00 00 00 00 
70   00 00 00 00 30 31 32 42 52 00 00 00 00 00 00 AC 
80   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
90   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
A0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Monitoring
------------------------------------------------------------------------------

Mainboard Model		Precision WorkStation 530 MT (0x9CA - 0x327C3840)

LPCIO
-----------------------------------------------------
Vendor			NS
Model			PC87365
Vendor ID		0xFF02
Chip ID			0xE5
Revision ID		0x8
Config Mode I/O address	0x2E

Dump config mode register space, LDN = 0x9
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   00 00 00 00 00 00 00 09 00 00 00 00 00 00 00 00 
10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
20   E5 11 1C 03 05 01 10 08 C2 00 C8 24 38 78 00 00 
30   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
60   0C 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   02 01 00 00 04 04 00 00 00 00 00 00 00 00 00 00 


PCI Device List
------------------------------------------------------------------------------

Host Bridge
bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2531
	Revision ID		0x04
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0xF0000000
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	AGP Capability
		Offset		A0h
		Version		2.0
		Status		enabled
		Transfer rate	4x (max 4x)
		Queue lenght	1 (max 32)
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 31 25 06 01 90 A0 04 00 00 06 00 00 00 00 
	 10   08 00 00 F0 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 A0 00 00 00 00 00 00 00 00 00 00 00 
	 40   D4 80 80 80 80 80 80 80 80 80 80 80 80 80 80 80 
	 50   05 2A 02 00 00 00 00 00 00 10 11 01 00 00 00 00 
	 60   10 00 10 00 10 00 10 00 10 00 10 00 10 00 10 00 
	 70   10 00 10 00 10 00 10 00 10 00 10 00 10 00 10 00 
	 80   00 00 00 00 00 00 00 00 0F 00 00 00 00 00 00 00 
	 90   03 00 03 00 61 00 01 08 55 19 00 00 81 0A 38 00 
	 A0   02 00 20 00 17 02 00 1F 04 03 00 00 00 00 00 00 
	 B0   80 00 00 00 20 00 00 00 00 50 04 00 20 10 89 00 
	 C0   44 C0 50 11 00 10 00 00 00 00 00 00 00 00 00 00 
	 D0   02 28 00 0E 03 00 00 33 AF 09 31 B5 01 00 03 00 
	 E0   00 00 00 00 00 00 00 00 2C 23 2B 33 07 00 00 00 
	 F0   00 00 01 00 74 FC 30 80 38 0F 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2532
	Revision ID		0x04
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 32 25 07 01 A0 00 04 00 04 06 00 40 01 00 
	 10   00 00 00 00 00 00 00 00 00 01 01 40 F0 00 A0 22 
	 20   00 FD F0 FD 00 F8 F0 F9 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 0E 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 2 (0x02), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2533
	Revision ID		0x04
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x02
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 33 25 07 01 A0 00 04 00 04 06 00 40 01 00 
	 10   00 00 00 00 00 00 00 00 00 02 03 00 F0 00 A0 22 
	 20   30 FE 50 FE F0 FF 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   02 28 00 0E 25 0E 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 30 (0x1E), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x244E
	Revision ID		0x04
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x04
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 4E 24 07 01 80 00 04 00 04 06 00 00 01 00 
	 10   00 00 00 00 00 00 00 00 00 04 04 40 E0 E0 80 22 
	 20   10 FE 20 FE F0 FF 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 
	 40   00 28 20 20 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   40 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 93 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   10 00 08 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   01 00 02 00 03 00 C0 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


PCI to ISA Bridge
bus 0 (0x00), device 31 (0x1F), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2440
	Revision ID		0x04
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 40 24 0F 00 80 02 04 00 01 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 08 00 00 10 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 81 08 00 00 10 00 00 00 
	 60   84 8A 80 8B 90 00 00 00 80 80 80 89 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   FF FC 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 40 00 00 00 00 00 
	 C0   00 00 00 00 04 08 00 00 00 00 00 00 01 00 00 00 
	 D0   86 21 00 00 02 18 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 C0 01 0C 0C 14 33 22 11 00 00 00 67 45 
	 F0   00 00 40 00 00 00 00 00 47 0F 00 00 00 00 00 02 


IDE Controller
bus 0 (0x00), device 31 (0x1F), function 1 (0x01)
Common header
	Vendor ID		0x8086
	Model ID		0x244B
	Revision ID		0x04
	PI			0x80
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x0000FFA0
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 4B 24 05 00 80 02 04 80 01 01 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   A1 FF 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   07 E3 03 E3 00 00 00 00 05 00 01 02 00 00 00 00 
	 50   00 00 00 00 10 14 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 31 (0x1F), function 2 (0x02)
Common header
	Vendor ID		0x8086
	Model ID		0x2442
	Revision ID		0x04
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x0000FF80
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x13
	Int. Pin		0x04
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 42 24 05 00 80 02 04 00 03 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   81 FF 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 13 04 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 2F 00 00 03 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


SMBus Controller
bus 0 (0x00), device 31 (0x1F), function 3 (0x03)
Common header
	Vendor ID		0x8086
	Model ID		0x2443
	Revision ID		0x04
	PI			0x00
	SubClass		0x05
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x0000DCD0
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x0A
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 43 24 01 00 80 02 04 00 05 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   D1 DC 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 0A 02 00 00 
	 40   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 31 (0x1F), function 4 (0x04)
Common header
	Vendor ID		0x8086
	Model ID		0x2444
	Revision ID		0x04
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x0000FF60
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x17
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 44 24 05 00 80 02 04 00 03 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   61 FF 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 17 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 2F 00 00 03 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


Audio device
bus 0 (0x00), device 31 (0x1F), function 5 (0x05)
Common header
	Vendor ID		0x8086
	Model ID		0x2445
	Revision ID		0x04
	PI			0x00
	SubClass		0x01
	BaseClass		0x04
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x0000D800
	Address 1 (port)	0x0000DC40
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x11
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 45 24 05 00 80 02 04 00 01 04 00 00 00 00 
	 10   01 D8 00 00 41 DC 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 11 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 47 0F 00 00 00 00 00 00 


VGA Controller
bus 1 (0x01), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x102B
	Model ID		0x0525
	Revision ID		0x82
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x10
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xF8000000
	Address 1 (memory)	0xFDEFC000
	Address 2 (memory)	0xFD000000
	Subvendor ID		0x102B
	Subsystem ID		0x0641
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		DCh
		Version		1.1
	AGP Capability
		Offset		F0h
		Version		2.0
		Status		enabled
		Transfer rate	4x (max 4x)
		Queue lenght	17 (max 32)
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   2B 10 25 05 07 00 90 02 82 00 00 03 10 40 00 00 
	 10   08 00 00 F8 00 C0 EF FD 00 00 00 FD 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 2B 10 41 06 
	 30   00 00 00 C1 DC 00 00 00 00 00 00 00 10 01 10 20 
	 40   60 15 54 40 08 3C 00 00 00 00 02 00 00 00 00 00 
	 50   00 AC 00 01 09 A4 90 00 06 00 00 80 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 01 F0 22 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   02 00 20 00 07 02 00 1F 04 03 00 1F 00 00 00 00 


PCI to PCI Bridge
bus 2 (0x02), device 31 (0x1F), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x1360
	Revision ID		0x03
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x02
	Secondary bus		0x03
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 60 13 07 01 20 00 03 00 04 06 00 00 01 00 
	 10   00 00 00 00 00 00 00 00 02 03 03 40 F0 00 A0 22 
	 20   40 FE 50 FE F0 FF 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 80 
	 40   00 68 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 30 0F 00 00 00 00 00 00 


System Device
bus 3 (0x03), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x1161
	Revision ID		0x01
	PI			0x20
	SubClass		0x00
	BaseClass		0x08
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xFE4FF000
	Subvendor ID		0x8086
	Subsystem ID		0x1161
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 61 11 00 00 00 00 01 20 00 08 00 00 80 00 
	 10   00 F0 4F FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 61 11 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Ethernet Controller
bus 4 (0x04), device 11 (0x0B), function 0 (0x00)
Common header
	Vendor ID		0x10B7
	Model ID		0x9200
	Revision ID		0x78
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x10
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (port)	0x0000EC80
	Address 1 (memory)	0xFE1FFC00
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x17
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		DCh
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   B7 10 00 92 17 01 10 02 78 00 00 02 10 40 00 00 
	 10   81 EC 00 00 00 FC 1F FE 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 20 FE DC 00 00 00 00 00 00 00 17 01 0A 0A 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 01 00 02 FE 
	 E0   00 41 00 68 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


OHCI FireWire Controller
bus 4 (0x04), device 12 (0x0C), function 0 (0x00)
Common header
	Vendor ID		0x104C
	Model ID		0x8020
	Revision ID		0x00
	PI			0x10
	SubClass		0x00
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE1FF000
	Address 1 (memory)	0xFE1F8000
	Subvendor ID		0x1028
	Subsystem ID		0x00D8
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		44h
		Version		1.0
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   4C 10 20 80 16 01 10 02 00 10 00 0C 10 40 00 00 
	 10   00 F0 1F FE 00 80 1F FE 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 28 10 D8 00 
	 30   00 00 00 00 44 00 00 00 00 00 00 00 10 01 02 04 
	 40   00 00 00 00 01 00 11 64 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 24 00 00 00 10 00 00 28 10 D8 00 00 00 00 00 


Communication Device
bus 4 (0x04), device 15 (0x0F), function 0 (0x00)
Common header
	Vendor ID		0x16EC
	Model ID		0x2F00
	Revision ID		0x01
	PI			0x00
	SubClass		0x80
	BaseClass		0x07
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE1E0000
	Address 1 (port)	0x0000EC78
	Subvendor ID		0x16EC
	Subsystem ID		0x010A
	Int. Line		0x13
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		40h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   EC 16 00 2F 07 01 90 02 01 00 80 07 00 40 00 00 
	 10   00 00 1E FE 79 EC 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 EC 16 0A 01 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 13 01 00 00 
	 40   01 00 22 48 00 00 00 00 52 12 01 00 01 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
------------------------------------------------------------------------------

DMI BIOS
--------
	vendor		Dell Computer Corporation
	version		A04
	date		10/13/2001


DMI System Information
----------------------
	manufacturer	Dell Computer Corporation
	product		Precision WorkStation 530 MT
	version		unknown
	serial		2FT1411
	UUID		44454C4C-46D81054-8031B2C0-4F343131


DMI Baseboard
-------------
	vendor		Dell Computer Corporation
	model		Precision WorkStation 530 MT
	revision	unknown
	serial		unknown


DMI System Enclosure
--------------------
	manufacturer	Dell Computer Corporation
	chassis type	Mini Tower
	chassis serial	2FT1411


DMI Processor
-------------
	manufacturer	Intel
	model		unknown
	clock speed	1500.0 MHz
	FSB speed	100.0 MHz
	multiplier	15.0x


DMI Processor
-------------
	manufacturer	Intel
	model		unknown
	clock speed	1500.0 MHz
	FSB speed	100.0 MHz
	multiplier	15.0x


DMI Port Connector
------------------
	designation	PARALLEL (internal)
	port type	Parallel Port PS/2
	connector	DB-25 female


DMI Port Connector
------------------
	designation	SERIAL1 (internal)
	port type	Serial Port 16550A
	connector	DB-9 male


DMI Port Connector
------------------
	designation	SERIAL2 (internal)
	port type	Serial Port 16550A
	connector	DB-9 male


DMI Port Connector
------------------
	designation	KYBD (internal)
	port type	Keyboard Port
	connector	PS/2


DMI Port Connector
------------------
	designation	MOUSE (internal)
	port type	Mouse Port
	connector	PS/2


DMI Port Connector
------------------
	designation	USB1 (internal)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB2 (internal)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB3 (internal)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB4 (internal)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	ENET (internal)
	port type	Network Port
	connector	RJ-45


DMI Port Connector
------------------
	designation	MIC (internal)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	LINE-OUT (internal)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	LINE-IN (internal)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	SCSI (internal)
	port type	SCSI Wide
	connector	68 Pin Dual Inline


DMI Port Connector
------------------
	designation	IEEE-1394 Front (internal)
	port type	Firewire (IEEE P1394)
	connector	IEEE 1394


DMI Port Connector
------------------
	designation	IEEE-1394 Back (internal)
	port type	Firewire (IEEE P1394)
	connector	IEEE 1394


DMI Extension Slot
------------------
	designation	PCI1
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI2
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI3
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI4
	type		PCI66
	width		64 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI5
	type		PCI66
	width		64 bits
	populated	no


DMI Extension Slot
------------------
	designation	AGP1
	type		AGP 4x
	width		32 bits
	populated	yes


DMI Physical Memory Array
-------------------------
	location	Motherboard
	usage		System Memory
	correction	Single-bit ECC
	max capacity	2048 MBytes
	max# of devices	4


DMI Memory Device
-----------------
	designation	RIMM_1 
	format		RIMM
	type		RDRAM
	total width	16 bits
	data width	16 bits
	size		128 MBytes


DMI Memory Device
-----------------
	designation	RIMM_2 
	format		RIMM
	type		RDRAM
	total width	16 bits
	data width	16 bits
	size		128 MBytes


DMI Memory Device
-----------------
	designation	RIMM_3 
	format		RIMM
	type		RDRAM
	data width	16 bits


DMI Memory Device
-----------------
	designation	RIMM_4 
	format		RIMM
	type		RDRAM
	data width	16 bits


Software
------------------------------------------------------------------------------

Windows Version		Microsoft Windows XP Professional  Service Pack 2 (Build 2600) 
DirectX Version		9.0c


Resources
------------------------------------------------------------------------------

Memory I/O Space, BA=0x00000000F0000000
Port I/O Space, BA=0xFFA0
Port I/O Space, BA=0xFF80
Port I/O Space, BA=0xDCD0
Port I/O Space, BA=0xFF60
Port I/O Space, BA=0xD800
Port I/O Space, BA=0xDC40
Memory I/O Space, BA=0x00000000F8000000
Memory I/O Space, BA=0x00000000FDEFC000
Memory I/O Space, BA=0x00000000FD000000
Memory I/O Space, BA=0x00000000FE4FF000
Port I/O Space, BA=0xEC80
Memory I/O Space, BA=0x00000000FE1FFC00
Memory I/O Space, BA=0x00000000FE1FF000
Memory I/O Space, BA=0x00000000FE1F8000
Memory I/O Space, BA=0x00000000FE1E0000
Port I/O Space, BA=0xEC78
Port I/O Space, BA=0x808, size=0x4
Memory I/O Space, BA=0x00000000FEE00000, size=0x1000
Port I/O Space, BA=0x2E

---

### Post by Junglizer on 2008-04-11
Well only having 256 megs of ram is fine for linux, however using some of the gui components (well gnome or kde, anyways) could be mildly problematic. Adding more ram, given that it is rambus may prove difficult, maybe not. Sometimes you can find it for cheap b/c no one wants it, however if it is a slightly older Dell (as it appears) you may have to buy it directly from them as untill recently they had proprietary RAM so you had to buy direct from them and pay out the bum.

---

### Post by amazingtaters on 2008-04-11
Same RAM as my old dimension. Ended up buying a new rig instead of payin over 500 bucks for RAM. Gave that old thing away to my grandma. You could run Xubuntu pretty solidly on that though I should think.

---

### Post by willfriedwald on 2008-04-11
thanks for the feedback again - 

another basic question:

the 530 has four RAM slots - two are filled with 128 each.

is it possible to put two more RAM chips in the additional slots of, say, 256 each?

or do all four have to be the same quantity? (I suspect the latter is true).  You can't have 256s & 128s at once, can you?

I found 128s on Froogle for $45, will also go on eBay and see what I can find... 

it would possibly be worth it two just add two more 128s - (or would it?) for a total of $90 - then I would have at least have HALF a gig - that should be enough for ubuntu? no?

---

### Post by Therion on 2008-04-11
> **willfriedwald said:**
> ... is it possible to put two more RAM chips in the additional slots of, say, 256 each?
Yes, you could do that.  If the modules are compatible, the SIZE doesn't matter.  No, really, this time size REALLY doesn't matter.  128's and 256's will operate side by side and in perfect harmony with one another.  Oh, and someone is sure to come along and tell you to put all the larger modules (the 256MB sticks) together, and in the primary channel.  It's a geek thing.  I've never noticed it making a difference, but I suppose, on paper, the math would support having the largest modules used first.

> **willfriedwald said:**
> it would possibly be worth it two just add two more 128s - (or would it?) for a total of $90 - then I would have at least have HALF a gig - that should be enough for ubuntu? no?
Well, it's a heck of an improvement.  Depends on if you want to separate yourself from $90 or not I guess.  My personal advice would be to cut your losses and get yourself a rig that uses more current specs... But I know that's not always an option.  Long story short, yes, you could dump in the extra RAM and most likely run Ubuntu with 512MB.  You might be better off though, using XUbuntu since it's lighter on the resource requirements.  It's impossible to say how well Ubuntu will run on your particular hardware profile, and only you can decide if the performance is acceptable or not.  Try plain-old-vanilla Ubuntu first, and if it's not snappy enough for you, fall back on XUbuntu.

Good luck!!

---

### Post by willfriedwald on 2008-04-11
would these work, do you think - I see that there are a bunch of them in different sets on eBay:

<http://cgi.ebay.com/Kingston-PC800-512MB-2x256MB-RDRAM-512-ECC_W0QQitemZ280215248807QQihZ018QQcategoryZ11152QQssPageNameZWDVWQQrdZ1QQcmdZViewItem>


KVR800X18/256 (x2) PLUS TWO C-RIMMS FREE	
Item number: 280215248807

currently at $32 - would put down a bid of $50 & see what happens - if I know they'll work on the 530...

thanks again

w

---

### Post by willfriedwald on 2008-04-13
am looking around at eBay... over all I think it's possible to get a gig (4 x 256) for $99 or 2 x 512 for $140.

then again, I saw a new cheapo PC for $199!  (with only 512 RAM - I would bet it would be $299 with 2GB maybe...) so that's tempting too.  

However, my main motivation was to find something useful to do with the Dell (like reanimating it with ubuntu) rather than simply trash it...  so we'll see.

thanks!

w

---

