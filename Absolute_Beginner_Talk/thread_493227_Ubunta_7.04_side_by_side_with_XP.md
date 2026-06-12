---
title: "Ubunta 7.04 side by side with XP?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by narvidh on 2007-07-05
Disgust with bill's proprietary world has led this semi-ignorant old man to seek an alternative.  
I would like to set up Linux side by side with an already existing XP. Can ubuntu 7.04 be installed on a system running XP.  
 I have a "Local Drive C" and a "Local Drive D"; I think my proccessor is Intel, although I don't know about that 64 bit part.  
Can somebody steer me in the right direction.  This whole open source thing started a couple years ago, when I heard of Firefox.  Glory be to the guys who are not bill or his ilk.

0OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Manufacturer	ASUSTek Computer INC.
System Model	P5GZ-MX
System Type	X86-based PC
Processor	x86 Family 15 Model 6 Stepping 5 GenuineIntel ~3199 Mhz
Processor	x86 Family 15 Model 6 Stepping 5 GenuineIntel ~3199 Mhz
BIOS Version/Date	American Megatrends Inc. 0601, 11/30/2006
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
Time Zone	Central Daylight Time
Total Physical Memory	1,024.00 MB
Available Physical Memory	563.76 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	2.39 GB
Page File	C:\pagefile.sys

---

### Post by Raineer on 2007-07-05
Sure. You just need some free space on the drive for Linux, it will detect the XP installation and setup a dual-boot menu.

If you need to resize or make new partitions, I recommend using the "GParted Live CD" which you can find via google.

---

### Post by stchman on 2007-07-05
> **narvidh said:**
> Disgust with bill's proprietary world has led this semi-ignorant old man to seek an alternative.  
I would like to set up Linux side by side with an already existing XP. Can ubuntu 7.04 be installed on a system running XP.  
 I have a "Local Drive C" and a "Local Drive D"; I think my proccessor is Intel, although I don't know about that 64 bit part.  
Can somebody steer me in the right direction.  This whole open source thing started a couple years ago, when I heard of Firefox.  Glory be to the guys who are not bill or his ilk.

0OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Manufacturer	ASUSTek Computer INC.
System Model	P5GZ-MX
System Type	X86-based PC
Processor	x86 Family 15 Model 6 Stepping 5 GenuineIntel ~3199 Mhz
Processor	x86 Family 15 Model 6 Stepping 5 GenuineIntel ~3199 Mhz
BIOS Version/Date	American Megatrends Inc. 0601, 11/30/2006
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
Time Zone	Central Daylight Time
Total Physical Memory	1,024.00 MB
Available Physical Memory	563.76 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	2.39 GB
Page File	C:\pagefile.sys

Yes, just make sure you have drive space that will be unallocated free space.  When installing tell Ubuntu to use the largest continuous free space.  It will setup Ubuntu and setup a boot loader called GRUB that will let you boot between Ubuntu and XP.

---

### Post by dnathe4th on 2007-07-05
Or use [wubi]("http://wubi-installer.org/")
thats what I did with my

it lets you install and uninstall ubuntu just like u do any other program in xp (or vista in my case)

---

### Post by az on 2007-07-05
> **Raineer said:**
> Sure. You just need some free space on the drive for Linux, it will detect the XP installation and setup a dual-boot menu.

If you need to resize or make new partitions, I recommend using the "GParted Live CD" which you can find via google.

By default, the Ubuntu install will offer to partition your drive for you.  You don't need to concern yourself with that stuff.  You may need to defragement your windows OS before you install Ubuntu.  If you boot the ubuntu installer and it doesn't offer you the option of creating room by shrinking your windows partition, reboot, defragment and try again.

But yes, you can dual-boot.  I reckon most people who first try Ubuntu do that.  It works just fine.

---

