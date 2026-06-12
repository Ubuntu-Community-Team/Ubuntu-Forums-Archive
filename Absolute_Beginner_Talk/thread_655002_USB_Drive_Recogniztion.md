---
title: "USB Drive Recogniztion"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by jonathonblake on 2007-12-31
I have a SimpleDrive PS portable USB disk drive 160 GB from Simpletech 
It works with Windows 2000.

I'm running Ubuntu 7.10 on a system with 1GB RAM.  I don't know the rest of the specs.  (It is from a local white box maker.)

I'm booting/using the LiveCD
I plug in the USB drive, I don't see anything that indicates that it is recognized.
The red light, which indicates that power is being drwn, does go on, on the external drive.

For those who want the data:

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf642d1e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   83  Linux
/dev/sda2             638        1275     5124735   82  Linux swap / Solaris
/dev/sda3            1276        1899     5012280   83  Linux
/dev/sda4            1900        4865    23824395    5  Extended
/dev/sda5            1900        3812    15366141   83  Linux
/dev/sda6            3813        4865     8458191   83  Linux

Disk /dev/sdb: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x741cacb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3932     1006576    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

###

sad1..sda6 is the hard drive on the system, that I want to copy the data off of, prior to reformatting the drive.
sdb1 is a 1 GB flash drive.  There are no issues with this drive.

Copying from "computer":
computer:///CD-RW%252FDVD-ROM%2520Drive.drive
computer:///14.7%2520GB%2520Volume.drive
computer:///4.8%2520GB%2520Volume.drive
computer:///4.9%2520GB%2520Volume.drive
computer:///8.1%2520GB%2520Volume.drive
computer:///USB%2520Flash%2520Memory.drive
computer:///Filesystem.desktop

#####
I did install NTF3 on the system.

The support for that hardware does not acknowledge the existence of Linux.  
(Would you trust any support tech that asks what version of Windows is required to run Linux?)  The supplied manual gives instructions for Windows and Macintosh.

Scouring the forums, and using Google, it looks like USB drives should be automatically recognized.    What am I missing to get Ubuntu to acknowledge this drive. 

xan

jonathon

---

### Post by mmb1 on 2007-12-31
Check to see if you have "usbutils" installed in synaptic.

---

### Post by mouseboyx on 2007-12-31
try pluging it in then rebooting

---

### Post by jonathonblake on 2008-01-02
> **mmb1 said:**
> Check to see if you have "usbutils" installed in synaptic.
USBUtils is installed.

> **mouseboyx  said:**
> 
try plugging it in then rebooting

That didn't have any effect.  :(

Both my USB wireless card, and my digital camera are detected.
The wireless card appears to work, but requires a password that I don't have access to, to access the network.

The photographs in the digital camera were automatically transferred.

xan

jonathon

---

### Post by finite9 on 2008-01-03
I have the same issue.  When I boot the LiveCD, it will not recognise my usb external drive but on two other laptops with a real installation of ubuntu gutsy and Debian lenny, the external usb drive is automounted in gnome.  sudo fdisk -l does not see the external usb drive at all.

---

