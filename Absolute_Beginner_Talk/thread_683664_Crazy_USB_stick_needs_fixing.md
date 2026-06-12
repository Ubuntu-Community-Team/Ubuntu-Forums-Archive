---
title: "Crazy USB stick needs fixing"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by belovedmonster on 2008-01-31
I tried to put a livecd on my memory stick without much luck and have now been trying to get the stick back to being a usuable 1GB memory stick again but through not really knowing what I am doing I have managed to screw it up.

As it stands at the moment:

When I insert it using Xubuntu it tells me its a 4GB Removable Memory (its 1GB!) When I click on this icon it tells me that it cant mount the drive. "Unknown Error"

When I load up Gparted it shows the device as being 235MB of unalloacted space. (When I was trying to make a USB LiveCD this is the size the Casper partition was once I had taken 750MB out for the live disk.) When I click to assign this space Gparted crashes.

When I use cfdisk it says:

```
 cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sda
                        Size: 1018165248 bytes, 1018 MB
              Heads: 32   Sectors per Track: 61   Cylinders: 1018

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   Linux                             1017.42 


```

Please help me make this crazy USB drive work!

---

### Post by Jidery on 2008-01-31
didyou test it under a dif operating system? it might be broken if it dosent work in any OS but only in ubuntu, then i say it needs reformating

---

### Post by belovedmonster on 2008-01-31
Last time I tried it with Windows it said it needed formatting and then said it couldnt format it. This was yesterday though and I've done a bunch of stuff to it since.

Anyways, I tried it again and Windows formatted it fine. Although it said it was 970MB. Is that the correct size for a 1GB pen?

I've just logged back into Xubuntu and it mounted perfectly, with the icon correctly saying its a 1GB drive. I copied some files across and Thunar says the properties are 316.7 MB full leaving 651.9 MB. So everything looks fixed.

Only...

Go into Gparted and it still says its 235MB unallocated. Weird!

---

### Post by belovedmonster on 2008-01-31
Also, I just tried cfdisk and got the following:

FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk
                          Press any key to exit cfdisk

---

### Post by dannyboy79 on 2008-01-31
you should probably just wipe it. I am guessing the partition table isn't correct. 
so do the following
plug it in
see where it get's mounted with this command
mount
this will show you a list of all folders and what partition or drive is mounted there. we now want to unmount it.
sudo umount /dev/sda1 (or /dev/sda)

then lets wipe it clean by writing zero's to it.
sudo dd if=/dev/zero of=/dev/Xda bs=521 count=1
NOTE: this command will WIPE your drive completely and write zero's to it. BE CAREFUL. Also, /dev/Xda should be changed to where ever your usb stick is located at, most likely /dev/sda. if you accidentally enter the wrong drive, you'll wipe it so again, BE CAREFUL.

After that, you should have a totally clean drive. now fire up gparted and create a partition and format it. done.

---

### Post by chronic on 2008-01-31
open up gnome partition editor (or w/e its called, im on osx at the mo) and format it as FAT32, make damn sure its fat32

---

### Post by belovedmonster on 2008-01-31
Mount does not bring up the drive. I tried fdisk -l instead and got this...

```
Disk /dev/sda: 1018 MB, 1018165248 bytes
32 heads, 61 sectors/track, 254 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I did the sudo dd if=/dev/zero of=/dev/sda bs=521 count=1 like you told me and it said

```
1+0 records in
1+0 records out
521 bytes (521 B) copied, 0.103404 seconds, 5.0 kB/s
```

After that the drive gives me an error message if I try to mount it. Because its empy?

I loaded up Gparted and it said dev/sda was still 235MB and unallocated. :confused: When I try to do anything with the allocation Gparted crashes.

---

### Post by wolfen69 on 2008-01-31
if gparted is crashing, do this: boot to live cd.

insert flash drive.
open terminal.
```
sudo su
```
```
fdisk -l
```
found out what flash drive is. probably sda1.
```
umount /dev/sda1
```
```
gparted
```
from pull down menu at top right select /dev/sda1.
delete all partitions.
format. done.

---

### Post by belovedmonster on 2008-01-31
I've been using the livecd all along :(

I did what you said and I got

```
root@ubuntu:/home/ubuntu# gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/hdd read-write (Read-only file system).  /dev/hdd has been opened read-only.
Unable to open /dev/hdd - unrecognised disk label.
Unable to open /dev/sda - unrecognised disk label.

```

In case it helps this is what fdisk -l gave me

```
Disk /dev/sda: 1018 MB, 1018165248 bytes
32 heads, 61 sectors/track, 254 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes
Disk identifier: 0x00034ca5

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by dannyboy79 on 2008-01-31
here's a previous thread about using fdisk, mkfs, and cfdisk from the command line since gparted isn't working for you.
[http://ubuntuforums.org/archive/index.php/t-346737.html](http://ubuntuforums.org/archive/index.php/t-346737.html)

---

### Post by belovedmonster on 2008-01-31
Thanks for the link, but I'm not sure which parts of it to use. 

I've been using fdisk to create new partitions all day but that doesnt seem to be working.

I'm getting to the point where I feel like I should just just get it back to being a usable 1GB stick and forget that Gparted keeps showing the casper drive. If I ever need to partition a usb stick I'll just buy a new one. :(

---

### Post by dannyboy79 on 2008-01-31
> **belovedmonster said:**
> Thanks for the link, but I'm not sure which parts of it to use. 

I've been using fdisk to create new partitions all day but that doesnt seem to be working.

I'm getting to the point where I feel like I should just just get it back to being a usable 1GB stick and forget that Gparted keeps showing the casper drive. If I ever need to partition a usb stick I'll just buy a new one. :(

well according to the fdisk -l you posted, it appears that the drive doesn't have any partitions. so you would create a new partition. then format it, then if you need to make it writable from within windows, you would use cfdisk. just follow the very end of the thread, that last 2 or 3 posts.

the dd=
command you did  before should have erased all data off the drive, including partition tables and everything.

---

### Post by belovedmonster on 2008-01-31
Thanks for your help. I've got it working though I know Gparted will show it as being weird if I try it. I'll just have to be content not to repartition it in the future :)

---

