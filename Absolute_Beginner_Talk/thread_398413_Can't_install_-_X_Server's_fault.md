---
title: "Can't install - X Server's fault"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Doctor-Alvis on 2007-04-01
Hello Linux pros, I'm in a pickle. I'm trying to install Ubuntu, with both "Start or install Ubuntu" and "Start Ubuntu in safe graphics mode", and I keep getting this error:

*Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?*


From what I gather, it has to do with my video card not being supported by default. I haven't been able to find anything to help with that though. The CD I burned got through the check with only 1 checksum error, is that an issue?

_Specs_ - Because it's good to know

CPU - AMD Athlon 64 X2 4600+ Windsor 2.4GHz 2 x 512KB L2 Cache Socket AM2 Processor

Graphics - EVGA 640-P2-N821-AR GeForce 8800GTS 640MB 320-bit GDDR3 PCI Express x16 HDCP Video Card

RAM -  Patriot eXtreme Performance 1GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory

Motherboard -  DFI LANPARTY UT NF590 SLI-M2R/G Socket AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard

HD -  Seagate Barracuda 7200.10 ST3320620AS (Perpendicular Recording Technology) 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive

_X server output_ - Just in case

Most of this stuff looks like standard date and version stats so I'm going to clip it out because I'm lazy:

[i](==) Log file: "/var/log/xorg.0.log", Time: Sat Mar 31 23:13:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found                     f"[/i]

I'm new to Linux, so be gentle. If you need any other info it's sitting right here. Looking pretty. Laughing at me.

Edit: Oh yeah, I've been having to use "noapic irqpoll noirqdebug" to get it going. I don't know if that effects anything or not.

---

### Post by nudnik on 2007-04-01
> **Doctor-Alvis said:**
> Hello Linux pros, I'm in a pickle. I'm trying to install Ubuntu, with both "Start or install Ubuntu" and "Start Ubuntu in safe graphics mode", and I keep getting this error:

*Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?*


From what I gather, it has to do with my video card not being supported by default. I haven't been able to find anything to help with that though. The CD I burned got through the check with only 1 checksum error, is that an issue?

_Specs_ - Because it's good to know

CPU - AMD Athlon 64 X2 4600+ Windsor 2.4GHz 2 x 512KB L2 Cache Socket AM2 Processor

Graphics - EVGA 640-P2-N821-AR GeForce 8800GTS 640MB 320-bit GDDR3 PCI Express x16 HDCP Video Card

RAM -  Patriot eXtreme Performance 1GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory

Motherboard -  DFI LANPARTY UT NF590 SLI-M2R/G Socket AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard

HD -  Seagate Barracuda 7200.10 ST3320620AS (Perpendicular Recording Technology) 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive

_X server output_ - Just in case

Most of this stuff looks like standard date and version stats so I'm going to clip it out because I'm lazy:

[i](==) Log file: "/var/log/xorg.0.log", Time: Sat Mar 31 23:13:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found                     f"[/i]

I'm new to Linux, so be gentle. If you need any other info it's sitting right here. Looking pretty. Laughing at me.

Edit: Oh yeah, I've been having to use "noapic irqpoll noirqdebug" to get it going. I don't know if that effects anything or not.

It looks as though perhaps your graphics hardware wasnt detected, but in the event things arent that disastrous, I offer the following:

sudo dpkg-reconfigure -phigh xserver-xorg

Input the above as root using the command line.

Your graphics card may be too new; support may not have been included yet. You might have better luck with "Feisty Fawn" the upcoming release of Ubuntu.

---

### Post by Doctor-Alvis on 2007-04-01
The command line - how do I get to that? Is it the same as the text mode I get when I hit escape at the options menu?

Edit: I found it.

---

### Post by Doctor-Alvis on 2007-04-01
Well, I couldn't get it to work but that's alright. I think I can wait until Feisty Fawn comes out.

---

