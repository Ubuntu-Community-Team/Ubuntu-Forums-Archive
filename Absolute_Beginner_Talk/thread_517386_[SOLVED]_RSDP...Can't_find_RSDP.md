---
title: "[SOLVED] RSDP...Can't find RSDP"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by holiday34691 on 2007-08-04
When I try to install unbuntu on an xp machine I keep getting 
can't find RSDP and the install stops.

---

### Post by apswartz on 2007-08-04
First try the alternate install CD and if needed add the "acpi=off"  to the command.

---

### Post by MrFSL on 2007-08-04
RSDP stands for: "Root System Description Pointer," which is a part of ACPI (Advanced Configuration and Power Interface), which[ "defines common interfaces for hardware recognition, motherboard and device configuration and power management."]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface")

If you have an older system (or buggy hardware) that does not support ACPI but does support APM (advanced power management) which is a legacy (i.e. older) power management system then you will have to perhaps disable acpi boot time. What type of computer are you installing on? What are the specs?

---

### Post by holiday34691 on 2007-08-04
First try the alternate install CD ?
I don't understand what that is. I have tried both the ubuntu and kubuntu install disks and keep getting the same error massage...can't find RSDP. 

What is the alternate install CD?

---

### Post by apswartz on 2007-08-04
> **holiday34691 said:**
> First try the alternate install CD ?
I don't understand what that is. I have tried both the ubuntu and kubuntu install disks and keep getting the same error massage...can't find RSDP. 

What is the alternate install CD?

Go to the download page...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

At the bottom there is a check box for the Alternate install disk.

---

### Post by holiday34691 on 2007-08-04
OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	BILL366
System Manufacturer	TriGem Computer, Inc.
System Model	COMO3
System Type	X86-based PC
Processor	x86 Family 6 Model 6 Stepping 5 GenuineIntel ~367 Mhz
BIOS Version/Date	American Megatrends Inc. 0631, 4/19/1999
SMBIOS Version	2.0
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name	BILL366\bill
Time Zone	Eastern Daylight Time
Total Physical Memory	256.00 MB
Available Physical Memory	26.59 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	618.57 MB
Page File	C:\pagefile.sys

---

### Post by MrFSL on 2007-08-04
Seems as though you are running on a slow Celeron system with 256MB of RAM. I don't think that you need to use the alternate CD, but I do think you will need to add acpi=off to your kernel boot line.

---

### Post by apswartz on 2007-08-04
If you need help changing the boot parameters go here...
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by holiday34691 on 2007-08-04
If you have an older system (or buggy hardware) that does not support ACPI but does support APM (advanced power management) which is a legacy (i.e. older) power management system then you will have to perhaps disable acpi boot time. What type of computer are you installing on? What are the specs?[/QUOTE]
-------------------------------------------------------
I corrected the RSDP problem by going into the BIOS/power setting file and enabled ACPI. Now we have progressed to...

hdc: error code: 0x70 sense_key: 0x05 asc; 0x64 ascq; 0x00...

/bin/sh; can't access tty; job control turned off; ](*,)

---

### Post by apswartz on 2007-08-04
hdc? How many hard drives are on your computer?

Anyway, this is supposed to be a fix...
[http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html](http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html)

---

### Post by xpod on 2007-08-04
I had the same issue myself once upon a time and just leaving it for a few minutes did the job in my case......it was an older systems too of course:)

It never actually prevented me getting Ubuntu onto the pc and i never had to use any of the boot parameters.It just carried on after a couple of mins thankfully.

I think i had the same message with the alternate cd too if i remember correctly?

---

### Post by holiday34691 on 2007-08-04
Two, C & D

---

### Post by apswartz on 2007-08-04
> **holiday34691 said:**
> Two, C & D
Then the first error you mentioned is pointing to your CD Drive.

---

### Post by holiday34691 on 2007-08-06
> **apswartz said:**
> First try the alternate install CD and if needed add the "acpi=off"  to the command.

The alternate install CD did the trick. 
Thanks

---

### Post by apswartz on 2007-08-06
Great!

---

