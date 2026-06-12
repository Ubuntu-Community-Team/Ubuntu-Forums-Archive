---
title: "Rank Noob ?s installing 6.10"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by monton on 2006-11-09
I am trying to install Ubuntu 6.10 to a P3-533, 224mb ram, 8.4gb hard drive, CD-Rom.

Hard drive has primary DOS partition and is formatted. Linux only no daul boot

1 Downloaded 6.10
2 Burned to disk
3 Set BIOS to boot from CD
4 Boot system doesn't boot from CD - No OS
5 Partition drive, Primary DOS
6 Boot system doesn't boot from CD - No OS
7 Format drive
8 Repeat 4 and 6 same
9 Reburn ubuntu_6.iso as bootable disc
10 Boot system - loads DR DOS but doesn't start install. Doesn't see valid FAT32 or NTFS file systems 

Should this disk not be partitioned? Is so as FAT32? Are there any command line switches to start install from A: prompt?
How to proceed....

Thanks, Monton:confused:

---

### Post by sitedesign on 2006-11-09
The 6.10 that you downloaded is an ISO. You need to write it to the disk as per the instructions on the Ubuntu downloads page.

Refer back to [www.ubuntu.com](www.ubuntu.com)

It sounds like you are writing the iso file to the disk as a data file then making it bootable which is wrong.
Let us know what software you are using to write the 6.10 disk.
Also which 6.10 version did you download (desktop or alternative)

---

### Post by jaytek13 on 2006-11-09
It doesn't make a difference whether it is partitioned before the install or not, nor does it make a difference in what format it is partitioned.

Do you have access to a different computer to test and see if the CD will boot there? 

I've run into problems with older cdrom drives that, while they would boot when first used, after however many years that capability just sort of disappeared from the drive.

---

### Post by monton on 2006-11-13
Thanks for your help and suggestions. Here is an update.

I copied the .iso file to disk - nice coaster
I made a "bootable" disk with the .iso file - made a nice set of coasters
Finally, burned image file - A keeper!

First attempt, well many attemps, to install on P3 533 system with 256MB RAM and 8.5gig HD would lock at 24%. Would run from disk but not install.

Next, AMD 1200 Thunderbird, 256MB, 60gig HD ATI AIW Radeon. Seems to install but gargled video. Even in "video safe mode".

Next, P3 800 256MB RAM 8.5gig HD. Installs flawlessly. Remove 60gig from T-Bird and install to P3 800 drive and again installs flawlessly. I'm sure it is a video driver issue but haven't had the time to investigate that further. Tomorrow I will be back at it.

While I haven't actually done anything productive I have to say I am impressed with Ubuntu. It is way more polished than I thought it would be.
On bootup it checked for updates and downloaded/installed them. I downloaded FireFox 2.0 and installed that. No glitches or problems other than my ineptness.

The amount and quality of the included software is impressive. I'm looking forward to educating myself on the OS. Rest assured I will be asking for help and guidance along the way and sharing what I learn.

Thanks to all that replied
Monton

Sorry if I sound overly polite but I live really close to Canada.......:D

---

### Post by monton on 2006-11-13
oh, and on the partition question.  I decided to run a W98 boot disk and used fdisk to remove all partitions. All the CD-ROMS were relatively new but I have had reading problems in other situations with old CR-ROMS.

I don't know why 6.10 wouldn't install on the P3 533.

thanks,
M

---

### Post by ReaderRat on 2006-11-13
> a P3-533, **224mb ram**, 8.4gb hard drive, CD-Rom.
It usually takes 256 Megs RAM to install the PC i386 version of Ubuntu. I would suggest that you download the Alternate CD. It installs in text mode and does not use as many resources. Or, you could try Xubuntu. It should only take 192 Megs RAM to install. 
Good luck, whatever you do...

---

