---
title: "Huge Mounting Problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by iamfromhuntersbar on 2007-12-19
Hi all!

I've got a Sony laptop that has suddenly stopped booting into windows, thus I've lost access to all my files. I'm using an ubuntu CD and hoping to just move my docs.

The laptop has 2 x 100GB HDDs in it and I'm guessing one is in a softRaid configuration. What I'd like to do is mount both drives, move all my files from the C: to the D: then format and re-install windows on the C: thus saving my files!

I'm new to BASH, so please bear with me.

When I try to mount sda1 I get;
> $MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


and when I try to mount sda2 I get;
> NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


When I fdisk the two drives I get;
> ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 8504 MB, 8504907264 bytes
255 heads, 63 sectors/track, 1033 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda2

Disk /dev/sda2: 100.0 GB, 100002954240 bytes
255 heads, 63 sectors/track, 12158 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3359d357

Disk /dev/sda2 doesn't contain a valid partition table


It's driving me crazy, Can anyone please shed some light?!

J

---

### Post by macogw on 2007-12-19
Go to Places > Computer and double click on the partitions you want to mount.

---

### Post by iamfromhuntersbar on 2007-12-20
Thanks for your reply!

When I go into places I only have "File System" and "89.2GB Volume" when I click on the latter it mounts, but I can't find any of my old files (I'm guessing this is my second HDD) and I still have no clue about my first!

---

