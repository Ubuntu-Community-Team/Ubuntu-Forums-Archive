---
title: "Partitioning"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Toulousse on 2007-05-22
Hi,

I have a new laptop with a single hard disk with my own boot loader that I would like to keep (BootItNG). 

The history goes something like this;

I installed windows XP,  I then installed the boot loader and reduced the size of the Windows XP partition and slid it to the end of the disk.  I then created a partition for Linux at the top of the disk (8 gig) immediately followed by a swap partition (1 gig).

The order of the partitions on the disk is as follows:

1) Linux
2) Linux Swap
....some unpartitioned space in between part 2 and part 3.....
3) WindowsXP

Next I started the Ubuntu install into partition 1 (Alternate 7.04), eventually I was prompted as to where I would like to install Grub.  The install message read (something like):
Select "(HD0)" to install to the MBR
Select "(HD0,1)" to install to the second partion

.... and this is where I'm getting confused, as per the instructions if I install into (HD0) then I fear I will wipe out the bootloader I want to keep, so logically the place I want to install the bootloader is in the first partition.... but how do I reference it ???, the instuctions above advise that (HDO,1) is the second partition.

Any help is greatly appreciated.

Thanks in advance

---

### Post by ronocdh on 2007-05-23
Hm, I'm really not sure, I've always used GRUB myself--haven't ever even bothered to setup LILO or ELILO, even though I'm on an EFI system. Anyhoo, I would try combing through the documentation for your chosen bootloader; surely someone thought of this problem!

Please post back with what you find, so others can benefit from it.

---

### Post by Ek0nomik on 2007-05-23
Why did you put Linux first on the disk?  Also, why do you have unpartitioned space?  It's a waste of space that could be put to use.

I only have 1 of my 3 computers dual booting.  I deleted all the partitions, and loaded the Windows XP disc.  I installed Windows XP (I think I gave it around 20GB, as Windows will grow the more you use it and room for programs/games).  Than I loaded up the Live CD and filled the rest of the drive with ext3 and a swap.  You shouldn't have any futzing around if you do it in that order.

---

