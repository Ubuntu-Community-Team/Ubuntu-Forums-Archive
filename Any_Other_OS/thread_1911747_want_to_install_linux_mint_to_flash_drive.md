---
title: "want to install linux mint to flash drive"
date: 2012-01-19
forum: Any Other OS
---

### Post by imachavel on 2012-01-19
```
fdisk /dev/sdx
fdisk: unable to open /dev/sdx: No such file or directory
danel@danel-Dimension-4700:~$ fdisk -l
danel@danel-Dimension-4700:~$ sudo fdisk -l
[sudo] password for danel: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32    31266815    15633392    c  W95 FAT32 (LBA)
```
```
danel@danel-Dimension-4700:~$ umount /dev/sdb1
danel@danel-Dimension-4700:~$ fdisk /dev/sdb1
fdisk: unable to open /dev/sdb1: Permission denied
danel@danel-Dimension-4700:~$ sudo fdisk /dev/sdb1

Command (m for help): p

Disk /dev/sdb1: 16.0 GB, 16008593408 bytes
64 heads, 32 sectors/track, 15266 cylinders, total 31266784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4, default 1): 
Using default value 1
First sector (2048-31266783, default 2048): a
First sector (2048-31266783, default 2048): 1
Value out of range.
```

I got this far, anyone know why that value is out of range??? THANKS

---

### Post by nothingspecial on 2012-01-19
Moved to Other OS/Distro talk.

---

### Post by imachavel on 2012-01-19
ok thanks

---

### Post by Double.J on 2012-01-19
Hi there, sorry I may be miss reading that, correct me if I did, but did you access sdb1 with fdisk and create a new partition? if so it need to be /dev/sdb then delete the partition on there then make new or format to new type etc.

Not to be pedantic, was there a reason for not using gparted? I just find I got a lot less errors when I can see the partition table?

---

### Post by imachavel on 2012-01-19
ok use gparted, create primary partition table, then try again??? Thanks. If I have any more errors I'll revisit this thread. and go over the commands one more time.

---

### Post by Double.J on 2012-01-19
> **imachavel said:**
> ok use gparted, create primary partition table, then try again??? Thanks. If I have any more errors I'll revisit this thread. and go over the commands one more time.

Hi there, use I use gparted, usually just erase all the partitions on it and start adding them again. as you want them, then install into those places :) 

Post back if you need any assistance - I'll be off to work shortly (barman) but others will be able to help and I'll check back before turning in :D

---

### Post by imachavel on 2012-01-19
I got stuck again:

```
 # umount /dev/sdb1
danel@danel-Dimension-4700:~$ fdisk /dev/sdb1
fdisk: unable to open /dev/sdb1: Permission denied
# danel@danel-Dimension-4700:~$ sudo fdisk /dev/sdb1
[sudo] password for danel: 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xc97052b0.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): a
Partition number (1-4): 

```I'm using this as a guide:

[http://forums.linuxmint.com/viewtopic.php?f=46&t=8780&hilit=usb+stick](http://forums.linuxmint.com/viewtopic.php?f=46&t=8780&hilit=usb+stick)

and keep getting stuck. well I'm a newb I guess ;)

---

### Post by nothingspecial on 2012-01-19
Please use code tags when posting terminal output. It is easier to read.

The easiest way to do this is to hilight the text then click the # in the formatting options at the top of the posting box.

---

### Post by imachavel on 2012-01-19
umm, when I entered # it said that a tag must be at least 3 characters long. I did what you said, at least what I thought you said

---

### Post by imachavel on 2012-01-19
little update:

syslinux -sf /dev/sdb1
syslinux: /dev/sdb1: Permission denied
danel@danel-Dimension-4700:~$ sudo syslinux -sf /dev/sdb1
[sudo] password for danel: 
syslinux: invalid media signature (not a FAT filesystem?)
danel@danel-Dimension-4700:~$ cd /downloads
bash: cd: /downloads: No such file or directory
danel@danel-Dimension-4700:~$ cd /downloads/
bash: cd: /downloads/: No such file or directory

I feel I'm almost there. I just need to mount that drive, then install linux mint .iso on it. I could be there very very very soon, but I'm not there yet. Haha why can't I cd to downloads?

btw why use sys linux is there a better command? It looks like syslinux does something with virtual code, I'm not sure if this is what I want to do, or is it?? Still using this:

[http://forums.linuxmint.com/viewtopic.php?f=46&t=8780&hilit=usb+stick](http://forums.linuxmint.com/viewtopic.php?f=46&t=8780&hilit=usb+stick)

best guide I've found so far.

---

