---
title: "Unable to install Ubuntu (or any Linux dist) on Amilo Xa 2528"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by davidtv on 2008-02-17
Just got myself a new laptop; an Amilo XA 2528, of course with Vista Home Premium pre-installed. I was looking forward to get rid of Vista and install Ubuntu right away, but  several problems has occured. 

Fujitsu Siemens Amilo Xa-2528
AMD Turion 64 X2 TL-60 @ 2 GHz (Dual core)
2GB DDR2-667 15-5-5-5 RAM
nVidia GeForce Go 8600 256 MB DDR2 up to 767MB TurboCache
320 GB SATA 5400 rpm

I have tried both the Alternate and the regular CD, but both gives me this message:

[I]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter "help" for a list of built-in dommands.

/bin/sh: can't access tty; job control turnd off
(initramfs)

[ 0.206515] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.588000 hda: drive not ready for command
37.620000 hda: drive not ready for command
37.620000 hda: drive not ready for command
[/I]

During the installation prosesses, I get to choose keyboard, and it starts to detect drives. Then it either hangs with a blue screens, or repeats the* 37.588000 hda: drive not ready for command* error message.

I've read the other threads here on the forum about the same laptop, and as far as I can see the problems are possibly that:


**- The disk is NTFS, not FAT32**
I've been using Ubuntu for a year and a half, but I'm a noob when it comes to partitioning disks and changing file systems. Several places on the net GParted is recommended for partitioning disks, and changing file systems. But as far as I can see, GParted is a Linux only program?
I downloaded and ran Cute Partitioning Manager, and it let me change the filesystem. So I changed to Ext3 on what in windows is "D:\", which resulted in that Vista didnt find the station. I tried to install Ubuntu again, but with the same results as above. Being afraid I'd ****** up, I changed the file system back NTFS on "D:\".

**- Ubuntu cannot find the DVD player**
In this thread (http://ubuntuforums.org/showthread.php?t=591143&highlight=amilo+2528&page=3" Vits thinks that Linux doesnt have the drivers for the DVD player.

In the same thread, It is suggested to try [www.InstaLinux.com](www.InstaLinux.com) and [www.wubi-installer-org](www.wubi-installer-org). Neither works, I just keep getting the same error message.

I am thinking about changing the file system on both hard disks, but I am afraid of doing something wrong. I would like to have a dual boot system, with Vista and Ubuntu.

Does anyone have any solutions to this? 
Should I change the file system to FAT32? If so, would that destroy my Vista installation? 
If I change file system on D:\, how do I get the Ubuntu installation process to install on that  partition?

Thanks for any help...

---

### Post by anewguy on 2008-02-17
You say "both drives", yet your spec only shows 1 physical drive, so I assume it is partitioned into 2 drives?

Could you post a listing of the drive partitions?

I believe (I don't use Vista, but have read here somewhere) that with Vista you are allowed to shrink the size of a partition.  If indeed you have 2 partitions (assuming 1 isn't the recovery partition!), try using Vista to shrink your second partition to where you have maybe 20 gig or so not allocated.  Don't change the type of the non-allocated partition - just leave it.  When you go to install LInux it should find that unused space and walk you through allocating it for Linux.

:)

---

### Post by xc3RnbFO8P on 2008-02-17
And you can read this:

> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182996)

---

### Post by davidtv on 2008-02-21
Hi, thanks for answering!

After another look, I've got two harddisks, both at 160 GB. One is partitioned in two, with Vista on one partition, and one named "system". The other is not partitioned. Both in NTFS format.

As for the link posted, I dont understand very much of it...

---

### Post by davidtv on 2008-02-21
I think the problem is that its trying to install Linux on the first hard drive, hda. How do I make it install on the second hard drive? Is that possible?

---

### Post by davidtv on 2008-02-22
After working on this issue for a week, Ive come to the conclusion that Linux doesnt recognize the hard disk controller. Ive tried Fedore, Mepis, OpenSuse and Ubuntu, and none works. A friend of mine offered to build a kernel that will work, but I think I'll wait some months and hope that the next version of Ubuntu will work on FSC.

Thanks for helping out :)

---

### Post by KiAnKo on 2008-04-26
I have the same problem. (I think it has to do with the old kernal used. You get the same problem with down-grading to WINDOWS XP, since drivers for SATA were unvailable in 2001, when XP came out.)

In order to install Linux you need to use [www.instalinux.com]("http://www.instalinux.com"), since not even Ubuntu 8.04 (from 080424) can be installed from LIVE-CD.

After installation, there is some problems with WLAN, DVD, WEBCAM etc. Some can solved by kernal update. The others by different solutions...

I have searched FSC & AMILO forums and UBUNTU forums in English, German and French... There is solutions, that will make FSC AMILO XA 2528 work with LINUX.

I'll put more info in my blog...

---

### Post by davidtv on 2008-05-01
Hi! Thanks for replying.

I've tried Instalinux.com several times, and the same problems happens then. 

I havent tried 8.04 yet, but will this spring. If you come up with some solutions, I'd be happy to know.

What's the link to your blog?

---

