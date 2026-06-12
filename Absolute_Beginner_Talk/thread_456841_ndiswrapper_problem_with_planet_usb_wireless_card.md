---
title: "ndiswrapper problem with planet usb wireless card"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by alcatris on 2007-05-28
Hi all. I'm using feisty on both my  laptop and desktop computer. 
On the laptop I was able to configure my wireless card (a Sis usb wireless card) using ndiswrapper but on the desktop system I was not able to configure it. ( a planet usb wireless card with atheros chipset)
here's the output from  ndiswrapper -l
athfmwdl : driver installed
        device (0CF3:0002) present
.
the output from lsusb
lsusb 
Bus 005 Device 002: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
.
When I start ndisgtk It tells me that hardware is not present ( although  ndiswrapper -l says otherwise) and when I open "Network settings" from System->Administration->System the wireless card is not in the list. 
    From what I have read till now. ndiswrapper does not work on x64 (my desktop computer is x64) but when I've installed ubuntu I've used the cd for x32.  Got any ideas on this?  

   PS.     The problem with ndisgtk reporting that hardware is not present I encounter on the laptop           computer but there I was able to configure the wifi card using network settings or
 "Network Manager Applet" and it works flawless ). the laptop is a pentium M x32. 

Here are the specs for the desktop machine:
SYSTEM INFORMATION
	Running Ubuntu Linux, the 4.0 release.
	GNOME: 2.18.1 (Ubuntu 2007-04-10)
	Kernel version: 2.6.20-16-generic (#2 SMP Wed May 23 01:46:23 UTC 2007)
	GCC: 4.1.2 (i486-linux-gnu)
	Xorg: 7.2.0 (04 April 2007)
CPU INFORMATION
	GenuineIntel, Intel(R) Pentium(R) 4 CPU 3.00GHz
	Number of CPUs: 2
	CPU clock currently at 2800.000 MHz with 2048 KB cache
	Numbering: family(15) model(4) stepping(3)
	Bogomips: 6026.99
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr

---

