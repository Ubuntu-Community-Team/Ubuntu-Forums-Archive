---
title: "Partitioning Mac HDD to share data between multi-boot OS"
date: 2007-10-01
forum: Apple Intel Users
---

### Post by shuttleworthwannabe on 2007-10-01
Hi, Thank you for helping out. I am in a bit confused about how to get my Mac drive partitioned so that I have a separate partition for OS X, WinXP, Ubuntu (all system files) and a separate common data partition for my personal data(documents mainly).
 
I am planning on getting a MBP with the 160G hdd (17"). I have some experience with partitioning the hdd because I dable a bit into linux systems (ubuntu mainly). I use QTParted or Gparted live CD to prepare the hdd for multibooting with XP. So I was wondering if I could not do the same with the machdd. For now I was just intending to install WinXP, then later Gutsy. Assume for now I am only doing this for WinXP/OS X dual boot with data sharing.

1. Can one use QTparted to partition the macHDD into smaller partitions?; by first formating the machdd cleanly. and have a disk map like this---(160G hdd size)

60 HFS+ for MacHDD|30 FAT32 for data|30 FAT32 for data|40 FAT32/NTFS for WinXP via bootcamp|

Once I have the drive formatted as above using the respective filesystems, I will then re-install OS X on partition#1; and then using bootcamp install windows XP on partition#4; the rest I will leave as it for inter-OS data exchange. Bootcamp says can't have more than 32G FAT32, hence these 2 partitions.

Can this be done using bootcamp? Any suggestions, recommendations? Much appreciated.

I did a thread search and also googled a bit, but did not get a straight forward answer. Hope you can help. I even posted on a Mac Forum, but they do not sem to know much about this.:confused:

thanks

---

### Post by pxwpxw on 2007-10-01
Decision #1.
 
Are you going with Apple GPT/MBR compatible partitioning (Macosx install default). If you opt for a straight MBR partitioning, Macosx will not install to MBR drive, but will boot and run on MBR, so that requires cloning an installed Macosx partition to the MBR drive.

If you omit the EFI primary partition, you probably will not be able to apply firmware updates ( my MacBook EFI firmware update used the EFI partition). 

For the GPT/MBR Apple scheme with EFI partition, maybe something like this, where Xp can see logical partitions.

MBR primary partitions
1 EFI reserved
2 OSX
3 WIN XP
4 Extended (remainder of the drive)

MBR Logical
 5 Common Data
 6 and above, Ubuntu, free space

EDIT: It is doubtful whether an extended and logical partitions can be created (say by windows XP) on an Apple GPT/MBR compatible disk. Gparted refuses to do it, maybe XP could. In any case the extended partition must be one of the 4 primaries, and partitions beyond the 4 primaries will not appear in the refit gptsync MBR list, only possibly in the GPT list.
Open to correction.

---

### Post by shuttleworthwannabe on 2007-10-01
> **pxwpxw said:**
> Decision #1.
 
Are you going with Apple GPT/MBR compatible partitioning (Macosx install default). If you opt for a straight MBR partitioning, Macosx will not install to MBR drive, but will boot and run on MBR, so that requires cloning an installed Macosx partition to the MBR drive.
 
If you omit the EFI primary partition, you probably will not be able to apply firmware updates ( my MacBook EFI firmware update used the EFI partition). 
 
For the GPT/MBR Apple scheme with EFI partition, maybe something like this, where Xp can see logical partitions.
 
MBR primary partitions
1 EFI reserved
2 OSX
3 WIN XP
4 Extended (remainder of the drive)
 
MBR Logical
5 Common Data
6 and above, Ubuntu, free space
 
px, thanks for the help;

Ys, I will want OS X as default OS and boot WinXp thru bootcamp; but was not sure how to create the thrid partition for data sharing. I searched a little more and came with [_[COLOR=#0000ff]this[/COLOR]_]("http://wiki.onmac.net/index.php/Extra_Partion"). It is still confusiong, but until I have the machine and OS X I will not know how difficult or easy it will be.

thanks

---

### Post by olliecampbell on 2007-10-01
Im just looking at this now too, but already have a triple booting system with free disk space that I cant use (for now!)

Bootcamp needs the HD to be in 1 big partition otherwise it wont install. So:

Install OSx on 1 large partition,
Install bootcamp
Partition so that you have the right space for OSx and leave the rest of the drive for XP.
Install Ubuntu and use its setup partitioning tool to cut down the XP partition size and setup any further partitions.


I think in theory that should work, I think (I did my installing ages ago!) thats what I did but it went wrong somewhere and now im stuck with this that im trying to sort out:



[http://ubuntuforums.org/showthread.php?t=564953](http://ubuntuforums.org/showthread.php?t=564953)

---

### Post by pxwpxw on 2007-10-02
**olliecampbell**

> 
Install OSx on 1 large partition,
Install bootcamp
Partition so that you have the right space for OSx and leave the rest of the drive for XP.
Install Ubuntu and use its setup partitioning tool to cut down the XP partition size and setup any further partitions.


I think in theory that should work, I think (I did my installing ages ago!) thats what I did but it went wrong somewhere and now im stuck with this that im trying to sort out:


There are howtos on ways to do triple boot partitioning, no comment on relative merits, but they address the main problem which is to do with the MBR partitioning scheme limitation to 4 primary partitions, and XP install quirks.


The catch comes after the 4th partition.
You have 

1. EFI
2. OSX
3. Ubuntu
4. XP

If these are all primary partittions as seen by the MBR system (XP), then any space beyond the 4th partition wil be inaccessible to XP and probably Gparted (for creating new partitions).
Linux and OSX don't have this problem in accessing additional partitions.

So the 4th partition has to be an MBR extended partition which can be subdivided into logical partitions, or else it can be a primary partition using all the remaining space.

So go carefully with trying your own partitioning scheme.:o

---

### Post by cyberdork33 on 2007-10-02
Gparted reads GPT just fine. It is really just windows that has the issues. I find that the best option is to have your / partition for linux (or /boot partition if you separate them) and windows in the first 4 (and the EFI partition 1st) anything else can go beyond the 4th partition without a problem. ANY partition that you want windows to access also has to be in the first four.

This can completely change if you convert to a MBR disk.

---

### Post by pxwpxw on 2007-10-04
> **shuttleworthwannabe said:**
> px, thanks for the help;

Ys, I will want OS X as default OS and boot WinXp thru bootcamp; but was not sure how to create the thrid partition for data sharing. I searched a little more and came with [_[COLOR=#0000ff]this[/COLOR]_]("http://wiki.onmac.net/index.php/Extra_Partion"). It is still confusiong, but until I have the machine and OS X I will not know how difficult or easy it will be.

thanks

Yes always helps to get hands-on results.
Second thoughts and **cyberdork33** comments, about the extended/logical incompatibility with GPT - see Edit above.

---

