---
title: "[SOLVED] GRUB in endless loop"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-10
I've had to modify the /etc/fstab, trying to make a brand new 320 gig drive have partitions unlike those that came over in a dd type of operation (G4L).

I was told to remove the # from in front of /dev/sda5.

After that on booting the only thing I see is the word GRUB, across the entire screen. One humongous endless loop.

---

### Post by SOULRiDER on 2007-12-10
This is a GRUB error, and a rather funny one too :-P
More info: [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

Just reinstall GRUB using a Live CD and it will be alright.

---

### Post by Mark_in_Hollywood on 2007-12-10
I'm running Gutsy v. 7.10. 

Can I use a Canonical LiveCD of Feisty or Dapper to "re"-GRUB the drives?

---

### Post by Mark_in_Hollywood on 2007-12-11
I don't know what question to ask, now. Grub has "failed", I guess. 

grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type is ext2fs, partition type 0x83

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

and:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36607   294045727   83  Linux
/dev/sda2           38393       38647     2048287+  82  Linux swap / Solaris
/dev/sda3   *       38648       38913     2136645   83  Linux
/dev/sda4           36608       38392    14338012+  83  Linux


HOW can I fix this?

---

### Post by Mark_in_Hollywood on 2007-12-13
This is an unrecoverable error. The OS had to be reinstalled.

---

