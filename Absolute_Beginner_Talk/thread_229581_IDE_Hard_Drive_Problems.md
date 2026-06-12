---
title: "IDE Hard Drive Problems"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by suilven222 on 2006-08-04
Hi,
I've just installed ubuntu 6.06 on my computer. It is a dual boot system with Windows XP, both OS's are on a single SATA drive. Its working great, except I have a second drive (IDE) which ubuntu is not recognising at all. Windows sees it fine. If i type fdisk -l it only lists my sata drive:

[INDENT]neil@neil-desktop:~$ for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done
Password:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17389   139677111    7  HPFS/NTFS
/dev/sda2           17390       17402      104422+  83  Linux
/dev/sda3           17403       19674    18249728+  83  Linux
/dev/sda4           19675       19929     2048287+  82  Linux swap / Solaris
[/INDENT]

Can anyone tell me why ubuntu doesn't recognise the IDE drive? It is formatted as NTFS at the moment, I have also tried FAT32 and leaving it unallocated but it made no difference. The /etc/fstab file has no reference to the drive since I cannot identify its device name so cannot add it!

I couldn't see anything on other forums on this problem. Thanks in advance.

Neil

---

### Post by gn2 on 2006-08-04
As a Linux noob, and not a dabbler in software tweakery I can't help with getting drie recognised - mounted?

BUT you could physically remove it from the PC case, stick it in an external USB enclosure (e.g. ICYBOX) and accsess the files on it that way?

---

