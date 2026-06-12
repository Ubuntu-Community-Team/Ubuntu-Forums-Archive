---
title: "HELP with Install to Dual Boot Laptop"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ZolaROM on 2007-07-12
I'm new to UBUNTU but not LINUX. It has been over 10 years since I configured a REDHAT PC>
I have an HP Pavillion DV9208nr and just installed a second SATA 120GB HDD just for LINUX.

I have the 7.04 CD and tried to install and configure from CD. However, it hangs and I'm gettin errors
"firmware helper[6476]:main.error loading /lib/firware/bcm43xx_microcode5.fa/ for device 
/class/firmware/0000:03.00.0 with driver (unknown)

[136.925040] bcmxx: Error: Microcode "bcm43xx_microcode5.fw not available load failed.

firmware helper [6511] [137.020128]

firmware helper [6528] [137.043016]

It does go on to load Kernal moduals, loads manual drivers, checks the file system, does an fsck 1.40-wip, mounts local file system, activates swap file, configures network interfaces....

Then it appears to stall with a black screen and I hear no disk activity nor see any HD activity LEDs blink.

A somewhat detailed configuration of my laptop:

A Western Digital 120GB SATA 2.5" HDD was added in the 2nd HDD drive compartment.

OS Name:                   Microsoftr Windows VistaT Home Premium 
OS Version:                6.0.6000 N/A Build 6000
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
OS Build Type:             Multiprocessor Free
Registered Organization:   Hewlett-Packard
Original Install Date:     5/22/2007, 6:00:47 PM
System Boot Time:          7/11/2007, 10:11:10 PM
System Manufacturer:       Hewlett-Packard
System Model:              HP Pavilion dv9208nr   
System Type:               X86-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: x64 Family 15 Model 72 Stepping 2 AuthenticAMD ~1600 Mhz
	AMD Turion(tm) 64 X2 Mobile Technology TL-50, 1600 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version:              Hewlett-Packard F.28    , 2/8/2007
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (GMT-05:00) Eastern Time (US & Canada)
Total Physical Memory:     1,918 MB
Available Physical Memory: 1,190 MB
Page File: Max Size:       4,058 MB
Page File: Available:      3,019 MB
Page File: In Use:         1,039 MB
     [27]: KB936824
Network Card(s):           2 NIC(s) Installed.
                           [01]: NVIDIA nForce Networking Controller
                                 Connection Name: Local Area Connection
                                 Status:          Media disconnected
                           [02]: Broadcom 802.11b/g WLAN
                                 Connection Name: Wireless Network Connection
                                 DHCP Enabled:    Yes
VIDEO INTERFACE:
Name	NVIDIA GeForce Go 6150
PNP Device ID	PCI\VEN_10DE&DEV_0244&SUBSYS_30B7103C&REV_A2\3&13C0B0C5&1&28
Adapter Type	GeForce Go 6150, NVIDIA compatible
Adapter Description	NVIDIA GeForce Go 6150
Adapter RAM	128.00 MB (134,217,728 bytes)
Installed Drivers	nvd3dum.dll
Driver Version	7.15.10.9815
INF File	oem40.inf (nv_C51M section)
Color Planes	Not Available
Color Table Entries	4294967296
Resolution	1024 x 768 x 59 hertz
Bits/Pixel	32
IRQ Channel	IRQ 18
Driver	c:\windows\system32\drivers\nvlddmkm.sys
 (7.15.10.9815, 4.26 MB (4,465,184 bytes), 2/27/2007 10:26 AM)

I have a suspicion that the video interface has something to do with some of this but I don't want to tweek anything without some sage advice from someone who has alot of experience with UBUNTU.

So... if your out there MR. Wizard could you kindly help ...

Thanks for your time reading this post!

MY Email:
[email]nw3n@netlogger.org[/email]

---

### Post by ReaderRat on 2007-07-12
Try this link about dual-booting:    [http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)
Scroll down to the boot option you need.

EDIT: Sorry, I just noticed you are using 2 HDDs.

---

### Post by eldepeche on 2007-07-12
You might try the alternate install cd, I have yet to use that and have it fail to install. It does exactly the same thing, but enters a text-based (think Debian) installer instead of the live cd environment.

---

### Post by ReaderRat on 2007-07-13
Dual-Boot, ALT CD Install, XP:[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

