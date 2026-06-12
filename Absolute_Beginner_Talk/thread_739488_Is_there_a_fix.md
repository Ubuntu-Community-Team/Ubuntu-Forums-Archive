---
title: "Is there a fix?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by richg on 2008-03-29
I am running Ubuntu 7.04 but now I am trying to setup another empty hard drive with 7.04.  . This happens with a 30gb and 80gb IDE hard drive. My PC is setup with a removable hard drive rack. I can remove the hard drive and install another one. Something has happended to my PC that I cannot figure out.
I have seen this error in the forums but no clear solution. Again, the hard drives are new.
When I try to boot from CD, here is what I am seeing for an error.
--------------------------------------------------------------------------------------------------

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3+0) Built-in shell (ash)
Enter 'help' for a list of built-in commands.


/bin/sh: can't access tty; job control turned off
(initramfs) flashing cursor at this point

Here are the PC specs.

Biostar P4M80-M4 Mobo

Socket 478
Supports Intel Pentium 4/Celeron D/Celeron Processor
Supports FSB 533/800MHz
Support Intel Hyper-Threading Technology
MEMORY
Support DDR 333/400 Mhz  I have 400 Mhz. RAM
2 x DDR DIMM Memory Slot                                             I have a total of 2gb RAM
Max. Supports up to 2GB MemoryEXPANSION SLOT
1 x CNR Slots
1 x AGP 8X Slots
3 x PCI SlotsLAN
VIA VT6103L - 10/100 PHYINTEGRATED VIDEO
VIA S3 UniChrome, On Board Graphic Max. Memory Share Up to 64MBCODEC
Realtek ALC655 6-Channel AC97 AudioINTERNAL I/O
1 x PS/2 Mouse
1 x PS/2 Keyboard
4 x USB Port
2 x USB Header
1 x COM Port
1 x Printer Port
1 x VGA Connector
1 x RJ-45 Port
3 x Audio Connector
2 x SATA Connector
2 x IDE Connector 
1 x Front Audio Header
1 x CD-IN Header
1 x S/PDIF-OUT Header
1 x CPU FAN Header
1 x System FAN Header
1 x Chassis Open HeaderDIMENSION
Micro ATX Form Factor Dimension: 20.2cm X 24.4cm ( W x L )ACCESSORIES
1 x IDE Cable
1 x FDD Cable
1 x I/O Shield
1 x CD Driver
1 x User Manual
-----------------------------------------------------------------------------------------------------------------
No floppy and floppy in bios is disabled.
Any thoughts? Thanks.

Rick

---

### Post by tgalati4 on 2008-03-29
Feisty uses UUID's to uniquely tag physical partitions and devices.  When you swap disks, GRUB can't find the kernel located at UUID=/dev/xxxxx.  You can remove the UUID's and go back to /dev/hda1 or /dev/sda1, but you have to change entries in /etc/fstab and in /boot/grub/menu.lst.

As far as the booting from the Live CD, have you run the Check CD option from the Live Disk on another computer?  Is this the same disk that you used to perform the installation?

---

### Post by richg on 2008-03-29
> **tgalati4 said:**
> Feisty uses UUID's to uniquely tag physical partitions and devices.  When you swap disks, GRUB can't find the kernel located at UUID=/dev/xxxxx.  You can remove the UUID's and go back to /dev/hda1 or /dev/sda1, but you have to change entries in /etc/fstab and in /boot/grub/menu.lst.

As far as the booting from the Live CD, have you run the Check CD option from the Live Disk on another computer?  Is this the same disk that you used to perform the installation?


Well that is good but you missed the part about a new hard drive. There is no Grub on it. When 7.04 came out I used the same DVD to install 7.04 on a hard drive. Now some months later, I cannot install 7.04 on a new hard drive again using the same DVD.

Rich

---

### Post by louieb on 2008-03-29
You get the  busy box prompt when things have gone wrong. I suspect the DVD may have a scratch in the wrong place. If you still have the ISO somewhere I'd burn another disk, run the media check option and try again. 
Good luck.

---

### Post by richg on 2008-03-30
I did not mention this before but the DVD runs Live CD on a 1.3g desktop and a 1.4 laptop very nice. The DVD was burned at 4X
I burned another ISO for 7.04 at 2x and I get the same error.
I burned a ISO for 7.10 and get the same error.
The two new ISOs run live very well on two other PCs.
Anything based on 7.04 causes the error on a blank hard drive and a good hard drive with 7.04 already on it.

I originally installed 7.04 with no problem. Something has happened to the PC.
It still runs 7.04 very well.

Rich

---

### Post by louieb on 2008-03-30
Since it worked before and as you say something has changed on the PC. :confused:DVD drive?  Think swapping out the DVD drive would be the next thing to do.

---

### Post by richg on 2008-04-16
I found out what caused the problem with mine. It was the DVD burner. I could run 6.0  live DVD but not anything based on Ubuntu 7.04. Also, I was beginning to have burn failures.

This may not apply to anyone else, but I will still mention, try replacing the burner.
Wish I had a better way to trouble shoot but maybe the techies will have some idea.

Rich:):)

---

