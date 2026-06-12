---
title: "extreme difficlties with ubuntu-install"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by [alterego] on 2007-02-02
Hi,
I really need your help in order to be able to install Ubuntu 6.10:

At first I tried to install the regular 6.10 i386 desktop but several times I got the well known error "Unknown fault or interupt at EIP 000 etc. etc.", which led me to think that perhaps I should update bios, drivers for my motherboard etc. - and I completed all the possible updates. After that I tried again to install the i386 but the same error came up again. This led me to the idead to download and try the Alternate-version, which I did.

When I tried to install the alternate-edition the same error came up no matter what.. I tried the commandline-setup, OEM, standard .. nothing has changed at all. The same error comes up.

It's really annoying and it frustrates me because I know how great Ubuntu really is and I want it on my computer!!

Any good ideas?? :)
Below are some information about my computer.. I'm really hoping for a solution to these problems very soon.
Thanks in advance.


[B]
BIOS:[/B]
Name : Phoenix - AwardBIOS v6.00PG
Version : IntelR - 42302e31
SerialNumber : CZB4480Y68
ReleaseDate : 11 / 04 / 2004
Target Operating System : Unknown
Language : n|US|iso8859-1
Status : OK[B]

CPU:[/B]
Name : Intel(R) Celeron(R) CPU 3.06GHz
Description: x86 Family 15 Model 4 Stepping 1
Manufacturer : GenuineIntel
Version : Model 4, Stepping 1
DataWidth : 32 Bits
Socket Designation : Socket 478
Type : Central Processor
CPU Id : BFEBFBFF00000F41
CPU Family : Unknown
CPU Stepping : 1
Load Percentage : 11 %
Max ClockSpeed : 3066 MHz
Current ClockSpeed : 3066 MHz
Voltage : 2.1 V
External Clock : 133 MHz
Upgrade Method : ZIF Socket
L2 Cache Size : 0 Kb
Display Availability : Running/Full Power
PowerManagement Supported : false
Status : OK

[B]
Harddisc:[/B]
Name : \\.\PHYSICALDRIVE0
Description: Diskdrev
Model : ST320011A
Manufacturer : (Standarddrive)
Number of Partitions : 2
Interface Type : IDE
TotalHeads : 255
TotalCylinders : 2434
TotalTracks : 620670
TotalSectors : 39102210
Tracks Per Cylinder : 255
Sectors Per Track : 63
Bytes Per Sector : 512 Bytes
Total Space : 19092 MB
Status : OK
[B]
Motherboard:[/B]
Name : Bundkort
Manufacturer : MICRO-STAR INTERNATIONAL CO., LTD
Product Name : Gamila/Giovani/Neon series
Version : 030
SerialNumber : 4A10033815

---

### Post by danielph on 2007-02-02
Extended Instruction Pointer is the register containing the memory location that the CPU is currently executing. I would maybe run a memory test (on CD boot) or if you have more than one memory chip pull them all and try one at a time.

When do you get the error and can you type it out exactly as it appears. Maybe able to find something on google if we can get it down exactly.

---

