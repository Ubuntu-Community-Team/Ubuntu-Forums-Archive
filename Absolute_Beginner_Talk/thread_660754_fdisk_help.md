---
title: "fdisk help"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by natman on 2008-01-07
I am trying to reformat a usb stick so that i can boot from it, i want to reformat it back to fat 16 1GB, but fdisk keeps giving premission denied heres my attempt.
[HTML]root@natman-desktop:/home/natman# fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1046 MB, 1046214656 bytes
33 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 2013 * 2048 = 4122624 bytes
Disk identifier: 0x000e06c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         253     1018456    6  FAT16
root@natman-desktop:/home/natman# fdisk /dev/sdb1
Note: sector size is 2048 (not 512)

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-252, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-252, default 252): 
Using default value 252

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
root@natman-desktop:/home/natman# 
[/HTML]
I also need to change the sector size to 512, any ideas, i have umounted and remounted the drive makes no diff

---

### Post by njparton on 2008-01-07
It's a long shot, but could gparted do this instead?

---

### Post by jflarm on 2008-01-07
Got a couple of suggestions...
Was the usb /dev/sdb1 partition mounted?
And I think the command should have been:
fdisk /dev/sdb

---

### Post by natman on 2008-01-07
I have tried gparted, but every time i try to create a new partition it crashs!, weather the drive is mounted or not, and i have tried both /dev/sdb and /dev/sdb1 doesnt seem to help

---

### Post by jflarm on 2008-01-07
I've never used gparted, only fdisk.
Did a little google and found this...
[http://www.cepros.com/linux/usb_flash_boot.html](http://www.cepros.com/linux/usb_flash_boot.html)
Do: fdisk -l /dev/sdb  ....in the tutorial on the page the partition was created even with that error shown.

---

### Post by njparton on 2008-01-07
> **natman said:**
> I have tried gparted, but every time i try to create a new partition it crashs!, weather the drive is mounted or not, and i have tried both /dev/sdb and /dev/sdb1 doesnt seem to help

Gparted is a little buggy in ubuntu I've found.  Try the gparted live cd as you can boot from it and it's quite stable.

---

### Post by hyper_ch on 2008-01-07
you need to 

```

sudo fdisk /dev/sdb1

```

---

### Post by hopelessone on 2008-01-07
Why would he sudo fdisk /dev/sdb1 is he's already root??

root@natman-desktop:/home/natman#

---

### Post by hyper_ch on 2008-01-07
> **hopelessone said:**
> Why would he sudo fdisk /dev/sdb1 is he's already root??

root@natman-desktop:/home/natman#

Bad, bad, bad ;)

didn't look at that and wondered why nobody said this before ;)

---

### Post by vanadium on 2008-01-07
Why do we need fdisk if all we need is to reformat the partition? If the partition table of the USB is not yet corrupt, then creating a fat 16 file system works with

sudo mkfs.msdos /dev/sdb1

with the necessary options to have 512 sector sizes. I am not sure if you can format a volume of 1 MByte with such small sector sizes, though. Either you will leave space unused, or If really needed, you will need to partition the USB anyway (there fdisk comes in) to smaller units.

---

### Post by rykel on 2008-06-22
Hi all,

I have been bugged by this problem all day.

I have a Creative Micro (MuVo) N200 MP3 player which I use as a 1GB thumbdrive. It has no data in it.

I am trying to install Ubuntu-Eee to it via isotostick.sh from startx.ro/sugar.

Unfortunately, I see so many ways to make the thumbdrive bootable until I am now confused.

GParted cannot seem to detect the device even though it is correctly mounted on the Desktop.

I also faced errors such as "sector is not 512"  and "Partition isn't marked bootable!" (isotostick error)... please help?

---

