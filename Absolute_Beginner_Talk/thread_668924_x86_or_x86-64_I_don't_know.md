---
title: "x86 or x86-64 I don't know"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by arai on 2008-01-15
how do I know if I have x86 or x86-64 based system? 

I am using Intel Pentium - D processor.

If it is x86-64 based, do I need to download AMD based Ubuntu CD for installation ?

Please clarify everything clearly. I am not a geek. thankyou.

---

### Post by nikoPSK on 2008-01-15
for AMD processor's get the amd version. x86 is basically intel, so get that. :)

---

### Post by Blutack on 2008-01-15
From
[http://en.wikipedia.org/wiki/Pentium_d](http://en.wikipedia.org/wiki/Pentium_d)
It appears you do have a 64 bit chip (x86_64).

64 bit Ubuntu will run on all 64 bit chips (with a few exceptions for weird server chips), AMD or Intel.  However, you can also run x86 Ubuntu on a x86_64 chip, you just aren't taking full advantage of it's capabilities.

This means you need to download the x86_64 version - 64bit AMD and Intel computers.

---

### Post by user1397 on 2008-01-15
> **arai said:**
> how do I know if I have x86 or x86-64 based system? 

I am using Intel Pentium - D processor.

If it is x86-64 based, do I need to download AMD based Ubuntu CD for installation ?

Please clarify everything clearly. I am not a geek. thankyou.the amd64 version works both for amd64 processorss and intel 64-bit processorss, such as the pentium D and core 2 duo lines.  you can download either one;  the x86 one is 32-bit and is usually the most recommended because 64-bit OS's have been known to have certain compatibility issues/programs that don't work,  but there are many guides in these forums that show you how to set up a 64-bit ubuntu system perfectly, and most of those problems have ceased to exist, so I would go for the 64 bit one.

---

### Post by ByteJuggler on 2008-01-15
> **arai said:**
> how do I know if I have x86 or x86-64 based system? 

I am using Intel Pentium - D processor.

If it is x86-64 based, do I need to download AMD based Ubuntu CD for installation ?

Please clarify everything clearly. I am not a geek. thankyou.

What model Pentium-D do you have?  You can download a Windows app (I asume you're still on Windows) called "Cpu-z" [here]("http://www.cpuid.com/cpuz.php") to identify your chip.  Then we'll be able to tell you what it supports for sure, but as others have noted it appears to support 64bit. Which means you can install either version.

---

### Post by Laibcoms on 2008-01-15
x86 is the most common architecture right now, and in my estimate about 70% of the applications you may want to use or need to use were built with the x86 architecture.  x86 is commonly known as 32-bit.

x86-64 is the 64-bit 'bridge', it isn't really a true 64-bit, but regardless, it is capable of running and doing and taking advantage of a true 64-bit architecture.  The advantage of x86-64 is that you can run both 32-bit and 64-bit on the machine provided the OS is 64-bit.  If your OS is 32-bit, you can of course only run 32-bit applications.  True 64-bit is still expensive and common only on the server side of things, not desktop/end-users.

x86-64 is also written as amd64; AMD64; Intel 64; x64 (x64 also happens to be the common name for true 64-bit).  Advantage of a 64-bit system is the usage of your memory/RAM, but which I doubt you'll care about ;)


So, once you figured out if your Pentium D is 64-bit (there is a 32-bit Pentium D, at least here in the Philippines), then you can choose which Ubuntu version you need.

If your Pentium D is 64-bit (which is the common P-D release), then I strongly suggest you use Ubuntu64.  Be warned though, as I said above, there will be applications that you won't be able to run/install, unless you know how to get around with it or recompile the application (which Im still figuring out myself :p ).  Overall, it is better to have a 64-bit OS, we're going that way anyway, better learn it now and be at the forefront among your peers :p

---

### Post by arai on 2008-01-15
here is what the report from this utility

Name Intel Pentium D 925
Code name Presler
Specification Intel Pentium D CPU 3.00 GHz
Cores 2

Update the full report is attached as a text document. please see it .

```
-------------------------
  CPU-Z version 1.43
-------------------------

Processors Map
------------------------------------------------------------------------------------

Number of processors	1
Number of threads	2

Processor 0
    -- Core 0
        -- Thread 0
    -- Core 1
        -- Thread 0


Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		2 (max 2)
Number of threads	2 (max 2)
Name			Intel Pentium D 925
Codename		Presler
Specification		Intel(R) Pentium(R) D CPU 3.00GHz
Package			Socket 775 LGA (platform ID = 2h)
CPUID			F.6.5
Extended CPUID		F.6
Core Stepping		D0
Technology		65 nm
Core Speed		2394.0 MHz (12.0 x 199.5 MHz)
Rated Bus speed		798.0 MHz
Stock frequency		3000 MHz
Instructions sets	MMX, SSE, SSE2, SSE3, EM64T
L1 Data cache		2 x 16 KBytes, 8-way set associative, 64-byte line size
Trace cache		2 x 12 Kuops, 8-way set associative
L2 cache		2 x 2048 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		yes
FID range		14.0x - 15.0x
VID range		1.116 V - 1.324 V
Features		XD


Thread dumps
------------------------------------------------------------------------------------

CPU Thread 0
APIC ID			0
Topology		Processor ID 0, Core ID 0, Thread ID 0
Type			01001008h
Max CPUID level		00000006h
Max CPUID ext. level	80000008h

Function		eax		ebx		ecx		edx
0x00000000		0x00000006	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F65	0x00020800	0x0000E49D	0xBFEBFBFF
0x00000002		0x605B5101	0x00000000	0x00000000	0x007D7040
0x00000003		0x00000000	0x00000000	0x00000000	0x00000000
0x00000004		0x04000121	0x01C0003F	0x0000001F	0x00000000
0x00000004		0x04000143	0x01C0103F	0x000007FF	0x00000000
0x00000005		0x00000040	0x00000040	0x00000000	0x00000000
0x00000006		0x00000000	0x00000000	0x00000000	0x00000000
0x80000000		0x80000008	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000001	0x20100000
0x80000002		0x20202020	0x20202020	0x20202020	0x6E492020
0x80000003		0x286C6574	0x50202952	0x69746E65	0x52286D75
0x80000004		0x20442029	0x20555043	0x30302E33	0x007A4847
0x80000005		0x00000000	0x00000000	0x00000000	0x00000000
0x80000006		0x00000000	0x00000000	0x08006040	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x00000000
0x80000008		0x00003024	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 D	16 KB	1 threads	
Cache descriptor	Level 2 U	2 MB	1 threads	
Cache descriptor	Level 1 T	12 KB	1 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00900
MSR 0x00000017		edx = 0x000A0000	eax = 0x00000000
MSR 0x0000002C		edx = 0x00000000	eax = 0x0C12030F
MSR 0x000001A0		edx = 0x00000000	eax = 0x22A50489
MSR 0x000001A1		edx = 0x00000000	eax = 0x00000000
MSR 0x00000198		edx = 0x00000F27	eax = 0x00000F27
MSR 0x00000199		edx = 0x00000000	eax = 0x00000F27

CPU Thread 1
APIC ID			1
Topology		Processor ID 0, Core ID 1, Thread ID 0
Type			01001008h
Max CPUID level		00000006h
Max CPUID ext. level	80000008h

Function		eax		ebx		ecx		edx
0x00000000		0x00000006	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F65	0x01020800	0x0000E49D	0xBFEBFBFF
0x00000002		0x605B5101	0x00000000	0x00000000	0x007D7040
0x00000003		0x00000000	0x00000000	0x00000000	0x00000000
0x00000004		0x04000121	0x01C0003F	0x0000001F	0x00000000
0x00000004		0x04000143	0x01C0103F	0x000007FF	0x00000000
0x00000005		0x00000040	0x00000040	0x00000000	0x00000000
0x00000006		0x00000000	0x00000000	0x00000000	0x00000000
0x80000000		0x80000008	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000001	0x20100000
0x80000002		0x20202020	0x20202020	0x20202020	0x6E492020
0x80000003		0x286C6574	0x50202952	0x69746E65	0x52286D75
0x80000004		0x20442029	0x20555043	0x30302E33	0x007A4847
0x80000005		0x00000000	0x00000000	0x00000000	0x00000000
0x80000006		0x00000000	0x00000000	0x08006040	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x00000000
0x80000008		0x00003024	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 D	16 KB	1 threads	
Cache descriptor	Level 2 U	2 MB	1 threads	
Cache descriptor	Level 1 T	12 KB	1 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00800
MSR 0x00000017		edx = 0x000A0000	eax = 0x00000000
MSR 0x0000002C		edx = 0x00000000	eax = 0x0C12030F
MSR 0x000001A0		edx = 0x00000000	eax = 0x22A50489
MSR 0x000001A1		edx = 0x00000000	eax = 0x00000000
MSR 0x00000198		edx = 0x00000F27	eax = 0x00000F27
MSR 0x00000199		edx = 0x00000000	eax = 0x00000F27


Chipset
------------------------------------------------------------------------------

Northbridge		Intel i945G/GZ rev. A2
Southbridge		Intel 82801GB (ICH7/R) rev. A1
Memory Type		DDR2
Memory Size		1024 MBytes
Channels		Single
Memory Frequency	332.5 MHz (3:5)
CAS#			5.0
RAS# to CAS#		5
RAS# Precharge		5
Cycle Time (tRAS)	15
Bank Cycle Time (tRC)	21


MCHBAR dump
-----------

Base address		0x0FED14000
Size			4096

       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
000   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
010   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
020   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
030   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
040   00 00 00 01 00 20 00 00 00 02 80 80 00 00 00 00 
050   01 00 8F 00 00 00 00 00 02 01 8F 00 00 00 00 00 
060   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
070   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
080   00 00 00 10 00 00 00 00 00 00 00 00 00 00 00 00 
090   55 50 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0A0   00 00 00 00 00 00 D8 00 00 00 00 00 00 00 00 00 
0B0   00 00 D8 00 00 00 00 00 00 00 00 00 00 00 D8 00 
0C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
100   10 20 20 20 00 00 00 00 33 00 00 00 07 00 00 00 
110   E8 38 40 DB 33 8C 78 54 5F 02 00 80 FF 01 FF 03 
120   06 4A 00 40 02 05 00 80 F0 11 00 00 00 00 00 00 
130   C4 06 00 00 6D 06 1A 87 01 02 08 00 00 00 00 00 
140   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
150   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
160   00 00 00 00 20 00 00 00 00 92 62 43 98 87 22 E0 
170   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
180   20 20 20 20 00 00 00 00 00 00 00 00 00 00 00 00 
190   E8 38 40 DB 33 8C 78 52 5F 02 00 80 FF 01 FF 03 
1A0   06 4A 00 40 02 04 00 00 F0 11 00 00 00 00 00 00 
1B0   C4 06 00 00 6D 06 1A 87 01 02 08 00 00 00 00 00 
1C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
1D0   00 00 00 00 00 00 00 00 00 00 00 00 80 00 00 00 
1E0   00 00 00 00 20 00 00 00 00 92 62 43 98 87 22 E0 
1F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
200   00 04 0F 00 00 00 00 00 30 01 02 04 08 00 00 00 
210   01 00 00 00 00 00 00 00 00 04 C0 A2 00 00 00 00 
220   64 03 00 03 00 30 02 01 00 31 00 00 00 00 00 00 
230   00 00 00 34 00 00 00 00 31 04 00 00 00 00 00 00 
240   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
250   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
260   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
270   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
280   00 00 00 00 40 40 02 10 00 00 00 00 00 00 00 00 
290   00 00 00 00 00 00 80 00 FF FF 03 FF FF 03 00 00 
2A0   08 00 00 00 00 00 00 00 FC 00 FF 03 00 00 00 00 
2B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
2C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
2D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
2E0   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
2F0   00 00 00 00 0C 00 00 00 CB 0A 05 00 00 00 00 00 
300   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
310   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
320   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
330   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
340   35 35 51 64 00 00 00 00 00 00 00 00 00 00 00 00 
350   00 41 00 A4 C5 57 56 32 00 00 FA BA 20 10 01 20 
360   00 00 00 00 FF FF 03 00 00 00 00 00 00 00 00 00 
370   00 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 
380   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
390   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
3A0   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
3B0   25 25 25 25 25 25 25 25 25 00 00 00 00 00 00 00 
3C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
3D0   00 41 00 00 00 00 00 32 00 00 9A 00 20 10 01 20 
3E0   00 00 00 00 FF FF 03 00 00 00 00 00 00 00 00 00 
3F0   00 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 
400   03 01 00 18 00 00 00 00 00 00 00 00 55 00 00 00 
410   44 00 00 88 00 00 00 00 33 00 00 88 00 00 00 00 
420   00 00 00 88 00 00 00 00 00 00 00 88 00 00 00 00 
430   44 00 00 88 00 00 00 00 44 00 00 88 00 00 00 00 
440   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
450   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
460   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
470   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
480   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
490   44 00 00 88 00 00 00 00 44 00 00 88 00 00 00 00 
4A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
4B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
4C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
4D0   00 00 00 00 27 26 25 26 2B 27 29 27 68 51 66 51 
4E0   26 25 26 27 51 66 51 68 17 1A 19 1A 00 00 00 00 
4F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
500   06 07 07 08 08 09 09 0A 0A 0B 0C 0D 0E 0F 10 12 
510   14 16 18 1A 1C 1E 20 22 24 26 28 2A 2D 30 34 39 
520   08 09 09 0A 0A 0B 0B 0C 0C 0D 0D 0E 0F 10 11 12 
530   13 15 17 19 1B 1D 1F 21 23 26 29 2D 31 35 39 3F 
540   04 04 05 05 06 07 09 0B 0D 0F 11 13 15 19 1B 1D 
550   1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 
560   0D 0D 0E 0E 0F 0F 0F 10 10 13 19 1B 1D 1F 1F 1F 
570   1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 1F 
580   06 06 07 07 08 0A 0C 0E 10 12 14 17 1A 1C 1E 20 
590   22 24 26 28 2A 2C 2E 30 32 34 36 38 3A 3C 3E 3F 
5A0   12 12 13 13 14 14 15 16 18 1A 1D 21 22 24 26 28 
5B0   2A 2C 2E 30 32 34 36 38 3A 3C 3E 3F 3F 3F 3F 3F 
5C0   06 06 07 07 08 0A 0C 0E 10 12 14 17 1A 1C 1E 20 
5D0   22 24 26 28 2A 2C 2E 30 32 34 36 38 3A 3C 3E 3F 
5E0   12 12 13 13 14 14 15 16 18 1A 1D 21 22 24 26 28 
5F0   2A 2C 2E 30 32 34 36 38 3A 3C 3E 3F 3F 3F 3F 3F 
600   0B 0B 0B 0C 0C 0C 0D 0D 0D 0E 0F 10 11 12 13 15 
610   17 19 1B 1D 1F 21 23 25 27 29 28 2A 2C 2E 30 32 
620   08 08 09 09 0A 0B 0B 0C 0D 0E 0F 10 11 12 13 14 
630   15 16 17 18 19 1A 1C 1E 20 22 24 26 28 2A 2C 2E 
640   0B 0B 0B 0C 0C 0C 0D 0D 0D 0E 0F 10 11 12 13 15 
650   17 19 1B 1D 1F 21 23 25 27 29 28 2A 2C 2E 30 32 
660   08 08 09 09 0A 0B 0B 0C 0D 0E 0F 10 11 12 13 14 
670   15 16 17 18 19 1A 1C 1E 20 22 24 26 28 2A 2C 2E 
680   06 07 07 08 08 09 09 0A 0A 0B 0C 0D 0E 0F 10 12 
690   14 16 18 1A 1C 1E 20 22 24 26 28 2A 2D 30 34 39 
6A0   08 09 09 0A 0A 0B 0B 0C 0C 0D 0D 0E 0F 10 11 12 
6B0   13 15 17 19 1B 1D 1F 21 23 26 29 2D 31 35 39 3F 
6C0   10 11 12 13 14 15 16 17 18 19 1A 1B 1C 1D 1E 1F 
6D0   20 21 22 23 24 25 26 27 28 29 2A 2B 2C 2D 2E 2F 
6E0   10 11 12 13 14 15 16 17 18 19 1A 1B 1C 1D 1E 1F 
6F0   20 21 22 23 24 25 26 27 28 29 2A 2B 2C 2D 2E 2F 
700   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
710   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
720   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
730   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
740   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
750   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
760   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
770   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
780   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
790   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
7F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
800   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
810   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
820   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
830   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
840   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
850   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
860   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
870   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
880   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
890   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
8F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
900   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
910   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
920   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
930   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
940   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
950   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
960   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
970   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
980   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
990   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
9F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A00   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AC0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AD0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
AF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B00   00 00 00 00 00 00 00 00 14 00 00 00 47 00 00 00 
B10   0C 00 00 00 1C 00 00 00 80 00 0C 02 00 00 00 00 
B20   00 00 00 00 47 14 1C 0C 00 00 00 00 00 00 00 00 
B30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B40   0C 0C 0C 0C 0C 0C 0C 0C 10 10 10 10 18 18 18 18 
B50   18 18 24 30 34 34 34 34 34 34 34 34 34 34 34 34 
B60   0E 0E 0E 0E 0E 0E 0E 0E 18 18 18 1A 1A 1A 1A 1C 
B70   1C 1C 1C 20 22 22 22 22 22 22 22 22 22 22 22 22 
B80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
BA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
BB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
BC0   00 22 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
BD0   00 FF FF CC CC 00 00 00 00 00 00 00 00 00 00 00 
BE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
BF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C00   32 00 00 20 01 01 01 01 00 00 00 00 00 00 00 00 
C10   00 00 00 00 03 02 80 00 1F 1F 2F 3E 00 00 54 42 
C20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
CA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
CB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
CC0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
CD0   00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 00 
CE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
CF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D00   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DC0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DD0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
DF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E00   00 00 00 00 00 00 00 00 BA 08 00 C6 00 00 00 00 
E10   89 74 8F 50 92 BF 1F 20 F5 49 6D 11 00 00 00 00 
E20   00 00 00 00 00 00 00 00 80 00 00 00 00 00 00 00 
E30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E50   00 00 80 28 F8 0D 02 00 77 77 77 00 00 00 00 00 
E60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
EA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
EB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
EC0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
ED0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
EE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
EF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F00   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F10   00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 
F20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F40   00 00 00 00 43 21 00 00 00 00 00 00 00 00 00 00 
F50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FA0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FB0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FC0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FD0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FE0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
FF0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Transcend Information (7F4F000000000000)
Size			1024 MBytes
Max bandwidth		PC2-5300 (333 MHz)
Part number		JM667QLJ-1G       
Serial number		0007ACDA
Manufacturing date	Week 38/Year 07

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		200	266	333	
CAS#			3.0	4.0	5.0	
RAS# to CAS# delay	3	4	5	
RAS# Precharge		3	4	5	
TRAS			9	12	15	
TRC			12	16	20	

Dump Module #1
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 30 45 00 82 08 00 00 
10   0C 04 38 01 02 00 07 3D 50 50 60 3C 1E 3C 2D 80 
20   20 27 10 17 3C 1E 1E 00 00 3C 69 80 18 22 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 76 
40   7F 4F 00 00 00 00 00 00 54 4A 4D 36 36 37 51 4C 
50   4A 2D 31 47 20 20 20 20 20 20 20 00 00 07 38 00 
60   07 AC DA 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   70 61 73 73 41 4D 44 38 4B 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Monitoring
------------------------------------------------------------------------------

Mainboard Model		D945GCNL (0x20A - 0x9ECDF4)

LPCIO
-----------------------------------------------------
Vendor			SMSC
Vendor ID		0x55
Chip ID			0x86
Config Mode I/O address	0x2E

Dump config mode register space, LDN = 0xA
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   00 00 00 00 00 00 00 0A 00 00 00 00 00 00 00 00 
10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
20   86 03 08 00 44 00 2E 00 00 00 00 00 00 00 00 00 
30   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
60   06 80 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI Device List
------------------------------------------------------------------------------

Host Bridge
bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2770
	Revision ID		0x02
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Vendor Dependant Capability
		Offset		E0h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 70 27 06 00 90 20 02 00 00 06 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 E0 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 90 D1 FE 01 40 D1 FE 03 00 00 F0 01 80 D1 FE 
	 50   00 00 30 00 09 00 00 00 00 00 00 00 00 00 00 00 
	 60   01 30 D1 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   10 11 11 11 11 33 33 00 FF 03 00 00 40 1A 39 00 
	 A0   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 91 00 00 00 
	 E0   09 00 09 51 0A E1 9B 98 07 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 03 00 00 00 00 00 


VGA Controller
bus 0 (0x00), device 2 (0x02), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x2772
	Revision ID		0x02
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0x50200000
	Address 1 (port)	0x000030E0
	Address 2 (memory)	0x40000000
	Address 3 (memory)	0x50280000
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	Message Signalled Interrupts Capability
		Offset		90h
	Power Management Capability
		Offset		D0h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 72 27 07 00 90 00 02 00 00 03 00 00 00 00 
	 10   00 00 20 50 E1 30 00 00 08 00 00 40 00 00 28 50 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 90 00 00 00 00 00 00 00 10 01 00 00 
	 40   00 00 00 00 E0 00 00 00 09 00 09 51 0A E1 9B 98 
	 50   07 00 30 00 09 00 00 00 00 00 00 00 00 00 80 3F 
	 60   00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   05 D0 00 00 00 00 7C AA 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   01 00 22 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   28 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   34 05 64 34 00 00 00 00 86 0F 03 00 00 00 00 00 


Multimedia device
bus 0 (0x00), device 27 (0x1B), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x27D8
	Revision ID		0x01
	PI			0x00
	SubClass		0x03
	BaseClass		0x04
	Cache Line		0x10
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0x502C0000
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x16
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
	Message Signalled Interrupts Capability
		Offset		60h
	PCI Express Capability
		Offset		70h
		Device type	Root Complex Integrated Endpoint Device
		Port		0
		Version		1.0
		Link width	0x (max 0x)
Extended capabilities
	Virtual Channel
		Offset		100h
	Root Complex Link Declaration
		Offset		130h
		Link Entries #	1
		Port Number	15
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 D8 27 06 00 10 00 01 00 03 04 10 00 00 00 
	 10   04 00 2C 50 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 16 01 00 00 
	 40   01 00 00 03 07 00 00 00 00 00 00 00 00 00 00 00 
	 50   01 60 42 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   05 70 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   10 00 91 00 00 00 00 00 00 08 10 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 
	100   02 00 01 13 01 00 00 00 00 00 00 00 00 00 00 00 
	110   00 00 00 00 01 00 00 80 00 00 00 00 00 00 00 00 
	120   80 00 00 81 00 00 00 00 00 00 00 00 00 00 00 00 
	130   05 00 01 00 00 01 02 0F 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 28 (0x1C), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x27D0
	Revision ID		0x01
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0x11
	Int. Pin		0x01
Capabilities
	PCI Express Capability
		Offset		40h
		Device type	Root Port of PCI-E Root Complex
		Port		1
		Version		1.0
		Physical slot	#0
		Presence detect	no
		Link width	0x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		90h
		Subsystem ID	0x27D0
		Sub. Vendor ID	0x8086
	Power Management Capability
		Offset		A0h
		Version		1.1
Extended capabilities
	Virtual Channel
		Offset		100h
	Root Complex Link Declaration
		Offset		180h
		Link Entries #	1
		Port Number	1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 D0 27 07 00 10 00 01 00 04 06 10 00 81 00 
	 10   00 00 00 00 00 00 00 00 00 01 01 00 F0 00 00 20 
	 20   F0 FF 00 00 F1 FF 01 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 11 01 04 00 
	 40   10 80 41 01 C0 0F 00 00 00 00 10 00 11 4C 11 01 
	 50   00 00 01 10 60 05 08 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 90 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   0D A0 00 00 86 80 D0 27 00 00 00 00 00 00 00 00 
	 A0   01 00 02 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00 
	 E0   00 00 C7 00 06 07 08 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 
	100   02 00 01 18 01 00 00 00 01 00 00 00 00 00 00 00 
	110   01 00 00 00 01 00 00 80 00 00 00 00 01 00 00 00 
	120   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	130   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 28 (0x1C), function 1 (0x01)
Common header
	Vendor ID		0x8086
	Model ID		0x27D2
	Revision ID		0x01
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x02
	Int. Line		0x10
	Int. Pin		0x02
Capabilities
	PCI Express Capability
		Offset		40h
		Device type	Root Port of PCI-E Root Complex
		Port		2
		Version		1.0
		Physical slot	#0
		Presence detect	yes
		Link width	1x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		90h
		Subsystem ID	0x27D2
		Sub. Vendor ID	0x8086
	Power Management Capability
		Offset		A0h
		Version		1.1
Extended capabilities
	Virtual Channel
		Offset		100h
	Root Complex Link Declaration
		Offset		180h
		Link Entries #	1
		Port Number	2
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 D2 27 07 00 10 00 01 00 04 06 10 00 81 00 
	 10   00 00 00 00 00 00 00 00 00 02 02 00 20 20 00 00 
	 20   10 50 10 50 F1 FF 01 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 10 02 04 00 
	 40   10 80 41 01 C0 0F 00 00 00 00 10 00 11 2C 11 02 
	 50   40 00 11 30 60 05 10 00 00 00 48 01 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 90 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   0D A0 00 00 86 80 D2 27 00 00 00 00 00 00 00 00 
	 A0   01 00 02 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00 
	 E0   00 00 C7 00 06 07 08 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 
	100   02 00 01 18 01 00 00 00 01 00 00 00 00 00 00 00 
	110   01 00 00 00 01 00 00 80 00 00 00 00 01 00 00 00 
	120   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	130   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 28 (0x1C), function 2 (0x02)
Common header
	Vendor ID		0x8086
	Model ID		0x27D4
	Revision ID		0x01
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x03
	Int. Line		0x12
	Int. Pin		0x03
Capabilities
	PCI Express Capability
		Offset		40h
		Device type	Root Port of PCI-E Root Complex
		Port		3
		Version		1.0
		Physical slot	#0
		Presence detect	no
		Link width	0x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		90h
		Subsystem ID	0x27D4
		Sub. Vendor ID	0x8086
	Power Management Capability
		Offset		A0h
		Version		1.1
Extended capabilities
	Virtual Channel
		Offset		100h
	Root Complex Link Declaration
		Offset		180h
		Link Entries #	1
		Port Number	3
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 D4 27 07 00 10 00 01 00 04 06 10 00 81 00 
	 10   00 00 00 00 00 00 00 00 00 03 03 00 F0 00 00 20 
	 20   F0 FF 00 00 F1 FF 01 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 12 03 04 00 
	 40   10 80 41 01 C0 0F 00 00 00 00 10 00 11 4C 11 03 
	 50   00 00 01 10 60 05 18 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 90 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   0D A0 00 00 86 80 D4 27 00 00 00 00 00 00 00 00 
	 A0   01 00 02 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00 
	 E0   00 00 C7 00 06 07 08 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 
	100   02 00 01 18 01 00 00 00 01 00 00 00 00 00 00 00 
	110   01 00 00 00 01 00 00 80 00 00 00 00 01 00 00 00 
	120   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	130   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 28 (0x1C), function 3 (0x03)
Common header
	Vendor ID		0x8086
	Model ID		0x27D6
	Revision ID		0x01
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x04
	Int. Line		0x13
	Int. Pin		0x04
Capabilities
	PCI Express Capability
		Offset		40h
		Device type	Root Port of PCI-E Root Complex
		Port		4
		Version		1.0
		Physical slot	#0
		Presence detect	no
		Link width	0x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		90h
		Subsystem ID	0x27D6
		Sub. Vendor ID	0x8086
	Power Management Capability
		Offset		A0h
		Version		1.1
Extended capabilities
	Virtual Channel
		Offset		100h
	Root Complex Link Declaration
		Offset		180h
		Link Entries #	1
		Port Number	4
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 D6 27 07 00 10 00 01 00 04 06 10 00 81 00 
	 10   00 00 00 00 00 00 00 00 00 04 04 00 F0 00 00 20 
	 20   F0 FF 00 00 F1 FF 01 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 13 04 04 00 
	 40   10 80 41 01 C0 0F 00 00 00 00 10 00 11 4C 11 04 
	 50   00 00 01 10 60 05 20 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 90 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   0D A0 00 00 86 80 D6 27 00 00 00 00 00 00 00 00 
	 A0   01 00 02 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00 
	 E0   00 00 C7 00 06 07 08 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 
	100   02 00 01 18 01 00 00 00 01 00 00 00 00 00 00 00 
	110   01 00 00 00 01 00 00 80 00 00 00 00 01 00 00 00 
	120   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	130   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 29 (0x1D), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x27C8
	Revision ID		0x01
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 4 (port)	0x00003080
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x17
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 C8 27 05 00 80 02 01 00 03 0C 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   81 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 17 01 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 27 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 29 (0x1D), function 1 (0x01)
Common header
	Vendor ID		0x8086
	Model ID		0x27C9
	Revision ID		0x01
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x00003060
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x13
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 C9 27 05 00 80 02 01 00 03 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   61 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 13 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 27 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 29 (0x1D), function 2 (0x02)
Common header
	Vendor ID		0x8086
	Model ID		0x27CA
	Revision ID		0x01
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x00003040
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x12
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 CA 27 05 00 80 02 01 00 03 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   41 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 12 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 27 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 29 (0x1D), function 3 (0x03)
Common header
	Vendor ID		0x8086
	Model ID		0x27CB
	Revision ID		0x01
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x00003020
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x10
	Int. Pin		0x04
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 CB 27 05 00 80 02 01 00 03 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   21 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 10 04 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 27 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


USB 2.0 Controller (EHCI)
bus 0 (0x00), device 29 (0x1D), function 7 (0x07)
Common header
	Vendor ID		0x8086
	Model ID		0x27CC
	Revision ID		0x01
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0x502C4000
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x17
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
	Debug Port Capability
		Offset		58h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 CC 27 06 00 90 02 01 20 03 0C 00 00 00 00 
	 10   00 40 2C 50 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 17 01 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   01 58 C2 C9 00 00 00 00 0A 00 A0 20 00 00 00 00 
	 60   20 20 00 00 00 00 00 00 01 00 00 00 00 00 00 C0 
	 70   00 00 C7 3F 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 AA FF 00 FF 00 FF 00 20 00 00 88 
	 E0   00 00 00 00 DB B6 6D 00 00 00 00 00 00 00 00 00 
	 F0   00 80 00 09 88 85 40 00 86 0F 01 00 0A 17 02 20 


PCI to PCI Bridge
bus 0 (0x00), device 30 (0x1E), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x244E
	Revision ID		0xE1
	PI			0x01
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x05
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	Subsystem Vendor Capability
		Offset		50h
		Subsystem ID	0xD606
		Sub. Vendor ID	0x8086
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 4E 24 07 00 10 00 E1 01 04 06 00 00 01 00 
	 10   00 00 00 00 00 00 00 00 00 05 05 20 10 10 80 22 
	 20   00 50 00 50 F1 FF 01 00 FF FF FF FF 00 00 00 00 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 FF 00 04 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 12 00 00 
	 50   0D 00 00 00 86 80 06 D6 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


PCI to ISA Bridge
bus 0 (0x00), device 31 (0x1F), function 0 (0x00)
Common header
	Vendor ID		0x8086
	Model ID		0x27B8
	Revision ID		0x01
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Vendor Dependant Capability
		Offset		E0h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 B8 27 07 00 10 02 01 00 01 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 E0 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 04 00 00 80 00 00 00 01 05 00 00 10 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   8B 8A 8A 89 D0 00 00 00 80 8A 89 8B 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   10 00 0F 3C 81 06 7C 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 02 04 00 31 00 00 00 13 00 00 00 00 03 00 00 
	 B0   00 00 F0 00 00 00 00 00 00 00 00 08 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   33 22 11 00 67 45 00 00 C0 C0 00 00 00 00 00 00 
	 E0   09 00 0C 10 A8 00 24 00 00 00 00 00 00 00 00 00 
	 F0   01 C0 D1 FE 00 00 00 00 86 0F 01 00 00 00 00 00 


IDE Controller
bus 0 (0x00), device 31 (0x1F), function 1 (0x01)
Common header
	Vendor ID		0x8086
	Model ID		0x27DF
	Revision ID		0x01
	PI			0x8A
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x000030B0
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x0A
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 DF 27 05 00 80 02 01 8A 01 01 00 00 00 00 
	 10   01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
	 20   B1 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 0A 01 00 00 
	 40   37 E3 00 00 0B 00 00 00 03 00 21 00 00 00 00 00 
	 50   00 00 00 00 12 10 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


IDE Controller
bus 0 (0x00), device 31 (0x1F), function 2 (0x02)
Common header
	Vendor ID		0x8086
	Model ID		0x27C0
	Revision ID		0x01
	PI			0x8F
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x000030C8
	Address 1 (port)	0x000030EC
	Address 2 (port)	0x000030C0
	Address 3 (port)	0x000030E8
	Address 4 (port)	0x000030A0
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x13
	Int. Pin		0x02
Capabilities
	Power Management Capability
		Offset		70h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 C0 27 05 00 B0 02 01 8F 01 01 00 00 00 00 
	 10   C9 30 00 00 ED 30 00 00 C1 30 00 00 E9 30 00 00 
	 20   A1 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 70 00 00 00 00 00 00 00 13 02 00 00 
	 40   00 80 00 80 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   01 00 02 40 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 0F 00 80 01 00 40 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 05 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


SMBus Controller
bus 0 (0x00), device 31 (0x1F), function 3 (0x03)
Common header
	Vendor ID		0x8086
	Model ID		0x27DA
	Revision ID		0x01
	PI			0x00
	SubClass		0x05
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x00003000
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x09
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   86 80 DA 27 01 00 80 02 01 00 05 0C 00 00 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   01 30 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 09 02 00 00 
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
	 F0   00 00 00 00 00 00 00 00 86 0F 01 00 00 00 00 00 


Ethernet Controller
bus 2 (0x02), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10EC
	Model ID		0x8168
	Revision ID		0x01
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x10
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x00002000
	Address 2 (memory)	0x50100000
	Subvendor ID		0x8086
	Subsystem ID		0xD606
	Int. Line		0x0A
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		40h
		Version		1.1
	Virtual Product Data Capability
		Offset		48h
	Message Signalled Interrupts Capability
		Offset		50h
	PCI Express Capability
		Offset		60h
		Device type	PCI-E Endpoint Device
		Port		0
		Version		1.0
		Link width	1x (max 1x)
	Vendor Dependant Capability
		Offset		84h
Extended capabilities
	Advanced Error Reporting Capability
		Offset		100h
	Virtual Channel
		Offset		12Ch
	Device Serial Number
		Offset		148h
	Power Budgeting Capability
		Offset		154h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   EC 10 68 81 00 00 10 00 01 00 00 02 10 00 00 00 
	 10   01 20 00 00 00 00 00 00 04 00 10 50 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 86 80 06 D6 
	 30   00 00 FE FF 40 00 00 00 00 00 00 00 0A 01 00 00 
	 40   01 48 C2 F7 03 00 00 00 03 50 00 00 00 00 00 00 
	 50   05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 84 01 00 63 7E 00 00 10 29 1A 00 11 F4 03 00 
	 70   40 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 09 00 4C 01 01 1C 02 00 FB FF FF 11 
	 90   08 30 00 00 01 0F 08 00 95 20 01 00 BF 00 00 00 
	 A0   02 28 FF 01 00 00 00 00 00 08 00 00 03 00 03 00 
	 B0   00 00 00 00 FF 3F FF 3F FF FF 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	100   01 00 C1 12 00 00 10 00 00 00 00 00 11 20 06 00 
	110   00 00 00 00 00 00 00 00 14 00 00 00 01 00 00 04 
	120   0F 19 00 00 08 00 01 02 6E E9 C1 DC 02 00 81 14 
	130   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Ethernet Controller
bus 5 (0x05), device 4 (0x04), function 0 (0x00)
Common header
	Vendor ID		0x10EC
	Model ID		0x8139
	Revision ID		0x10
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x00
	Latency			0x20
	Header			0x00
PCI header
	Address 0 (port)	0x00001100
	Address 1 (memory)	0x50001000
	Subvendor ID		0x11F6
	Subsystem ID		0x8139
	Int. Line		0x0B
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   EC 10 39 81 00 00 90 02 10 00 00 02 00 20 00 00 
	 10   01 11 00 00 00 10 00 50 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 F6 11 39 81 
	 30   00 00 FF FF 50 00 00 00 00 00 00 00 0B 01 20 40 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   01 00 C2 F7 03 00 00 00 00 00 00 00 00 00 00 00 
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


Modem
bus 5 (0x05), device 5 (0x05), function 0 (0x00)
Common header
	Vendor ID		0x1057
	Model ID		0x3052
	Revision ID		0x04
	PI			0x00
	SubClass		0x03
	BaseClass		0x07
	Cache Line		0x10
	Latency			0x20
	Header			0x00
PCI header
	Address 0 (memory)	0x50000000
	Address 1 (port)	0x00001000
	Subvendor ID		0x1057
	Subsystem ID		0x3020
	Int. Line		0x0B
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   57 10 52 30 97 02 90 02 04 00 03 07 10 20 00 00 
	 10   00 00 00 50 01 10 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 57 10 20 30 
	 30   00 00 00 00 80 00 00 00 00 00 00 00 0B 01 01 3E 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   01 00 42 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
------------------------------------------------------------------------------

DMI Processor
-------------
	manufacturer	Intel(R) Corporation
	model		Intel(R) Pentium(R) D CPU 3.00GHz
	clock speed	3000.0MHz
	FSB speed	200.0MHz
	multiplier	15.0x


DMI BIOS
--------
	vendor		Intel Corp.
	version		NL94510J.86A.0017.2007.0828.1137
	date		08/28/2007


DMI System Information
----------------------
	manufacturer	unknown
	product		unknown
	version		unknown
	serial		unknown
	UUID		7F29DC74-725B11DC-B98B00E0-188501F7


DMI Baseboard
-------------
	vendor		Intel Corporation
	model		D945GCNL
	revision	AAD97184-105
	serial		BTNL73901NGJ


DMI System Enclosure
--------------------
	manufacturer	unknown
	chassis type	2X
	chassis serial	unknown


DMI Port Connector
------------------
	designation	PRIMARY (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SECONDARY (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	ATX_PWR (internal)


DMI Extension Slot
------------------
	designation	PCIE X16 SLOT
	type		A5
	populated	no


DMI Extension Slot
------------------
	designation	PCIE X1 SLOT 1
	type		A5
	populated	yes


DMI Extension Slot
------------------
	designation	PCI SLOT 1
	type		PCI
	width		32 bits
	populated	yes


DMI Extension Slot
------------------
	designation	PCI SLOT 2
	type		PCI
	width		32 bits
	populated	yes


DMI Physical Memory Array
-------------------------
	location	Motherboard
	usage		System Memory
	correction	None
	max capacity	4096MBytes
	max# of devices	2


DMI Memory Device
-----------------
	designation	J6H1
	format		DIMM
	type		unknown
	total width	64bits
	data width	64bits
	size		1024MBytes


DMI Memory Device
-----------------
	designation	J6J1
	format		DIMM
	type		unknown


Software
------------------------------------------------------------------------------

Windows Version		Microsoft Windows XP Professional  Service Pack 2 (Build 2600) 
DirectX Version		9.0c


Resources
------------------------------------------------------------------------------

Memory I/O Space, BA=0x0000000050200000
Port I/O Space, BA=0x30E0
Memory I/O Space, BA=0x0000000040000000
Memory I/O Space, BA=0x0000000050280000
Memory I/O Space, BA=0x00000000502C0000
Port I/O Space, BA=0x3080
Port I/O Space, BA=0x3060
Port I/O Space, BA=0x3040
Port I/O Space, BA=0x3020
Memory I/O Space, BA=0x00000000502C4000
Port I/O Space, BA=0x30B0
Port I/O Space, BA=0x30C8
Port I/O Space, BA=0x30EC
Port I/O Space, BA=0x30C0
Port I/O Space, BA=0x30E8
Port I/O Space, BA=0x30A0
Port I/O Space, BA=0x3000
Port I/O Space, BA=0x2000
Memory I/O Space, BA=0x0000000050100000
Port I/O Space, BA=0x1100
Memory I/O Space, BA=0x0000000050001000
Memory I/O Space, BA=0x0000000050000000
Port I/O Space, BA=0x1000
Memory I/O Space, BA=0x00000000F0000000, size=0x1000
Port I/O Space, BA=0x408, size=0x4
Memory I/O Space, BA=0x00000000FEE00000, size=0x1000
Memory I/O Space, BA=0x00000000FED14000, size=0x1000
Memory I/O Space, BA=0x00000000FED1C000
Port I/O Space, BA=0x500, size=0x3C
Port I/O Space, BA=0x680
Port I/O Space, BA=0x2E

```

---

### Post by Victormd on 2008-01-15
Both the x86 and AMD64 are great systems. However, you might want to take into account the following: considering that you are a beginner, you might want to install the 32bit version (x86), there is more support and less work-arounds to get everyting up and running. As for taking full advantage of your 64bit processor, unless you intend to do alot of graphical work, you won't notice any difference between the two (x86 vs 64bit)... Now, if you want to get your hands dirty and work a bit to have a smooth system, install the 64bit version, you'll learn alot! However, as mentioned above, the AMD64 might not work on ALL 64bit intel based comps. so you'll have to try it (I don't know of any tools to check compatibility)

---

### Post by ByteJuggler on 2008-01-16
> **arai said:**
> here is what the report from this utility
```

.
.
.
Instructions sets	MMX, SSE, SSE2, SSE3, EM64T
.
.
.

```


That "EMT64" there says your chip is 64bit capable.  So it's confirmed.  

Whether you use the 32-bit or 64-bit version is largely up to whether you
a) have 4GB or more RAM
b) have specific 64-bit apps you want to run.

If the answer to both those questions is no, then I'd suggest installing the 32-bit version, as it's slightly better supported still compared to 64-bit.

---

### Post by ByteJuggler on 2008-01-16
> **Victormd said:**
>  However, as mentioned above, the AMD64 might not work on ALL 64bit intel based comps. so you'll have to try it (I don't know of any tools to check compatibility)

Umm just to clarify:

AMD64=EMT64=64bit=x64

So please note: There is only one 64bit instruction set for the x86 architecture chips.  It was originally created by AMD, which is why it's sometimes referred to as AMD64, and sometimes as x64 (due I guess Microsoft using that term.)  Intel, being Intel, decided to name it EMT64 (they could not possibly be seen to be having the AMD name in a part of their chips now could they!?), but all three terms refer to exactly the same thing -- the 64bit instruction set standard originally implemented by AMD.

---

