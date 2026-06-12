---
title: "Some questions regarding installing Ubuntu next to Win XP"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by WardB on 2007-09-27
OK, I've tried the 7.04 from the Live CD.   Booted without problems, so i'd like to install it, but like many Win XP users, I have some questions regarding Ubuntu prior to intalling it.  I'm planning to buy an extra hard disk to install linux on it, so i don't mess up the XP installation.

I'll try to phrase my Q's so that hopefully a short answer is possible.

Q1: What filesystem do I best use?  Ideally, I should be able to read in Linux from my XP partition and vice versa, if that's possible.  I'd like to point out that my XP partition is on a SATA RAID ( with NVIDIA RAID controller/drivers ). Does that matter for linux?
Q2: What happens with GRUB if I reformat the Linux HD so I end up again with only XP?  **Can I just use the XP boot loader instead of GRUB and never install GRUB?  **
Q3: 64 bit or 32 bit version?  If I install the 64 bit version of UBUNTU, do I have to have 64 bit drivers and 64 bit versions of software?  Will 32 bit versions work on it?

---

### Post by hyper_ch on 2007-09-27
Q1: If you don't know what filesystem to use, then use the default one (ext3). You need at least two partitions: 1x SWAP and 1x ROOT... however I recommend a third huge one as "/HOME".

Ubuntu can by default read the windows partitions but not write to it.
Windows can by default neither read nor write to EXT3 partitions.
There is ntfs-3g that will allow you to write to the windows drives form Ubuntu.
There are drivers that will allow you to read/write to ext3 partitions from windows.

Q2: Nothing happens to grub as grub will install itself in the first partition of the first booting harddisk... they way you make it sound like you will not assign the new harddisk as first one so grub will overwrite the windows boot manager... as far as I know the M$ boot loader can't load any linux.

---

### Post by giox on 2007-09-27
> **WardB said:**
> OK, I've tried the 7.04 from the Live CD.   Booted without problems, so i'd like to install it, but like many Win XP users, I have some questions regarding Ubuntu prior to intalling it.  I'm planning to buy an extra hard disk to install linux on it, so i don't mess up the XP installation.

I'll try to phrase my Q's so that hopefully a short answer is possible.

Q1: What filesystem do I best use?  Ideally, I should be able to read in Linux from my XP partition and vice versa, if that's possible.  I'd like to point out that my XP partition is on a SATA RAID ( with NVIDIA RAID controller/drivers ). Does that matter for linux?
Q2: What happens with GRUB if I reformat the Linux HD so I end up again with only XP?  **Can I just use the XP boot loader instead of GRUB and never install GRUB?  **
Q3: 64 bit or 32 bit version?  If I install the 64 bit version of UBUNTU, do I have to have 64 bit drivers and 64 bit versions of software?  Will 32 bit versions work on it?

1. The best file system with ubuntu I will say is ext3 and one swap atleast two time the amount of ram you have. Ubuntu will be able to read and write on your XP partition, but not the other way. But to do that you have to install NFTS support from Synaptic or Add and Remove program what ever is easier for you. To let you know when you install it Ubuntu will ask you what you want to do with you HD. You can use the option that ubuntu will resize you hard drive and install a dual boot with grub. I guess you know that but just to refresh.
2. I cant answer that question but i am sure somebody else will.

3. I will say use the 32 bit Version. I think is more drivers and software support for it. Again thats what i think.

But if you are planning to buy a new hard drive go for it then you can play more with ubuntu and if you mess it up just reload without worries about your other partition. Then when you get used to it get rid of windows. :lolflag:

---

