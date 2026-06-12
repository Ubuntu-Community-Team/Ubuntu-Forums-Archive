---
title: "ntfsresize: making the big switch"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by diamond on 2006-07-29
I'm not really a beginner with Ubuntu, but this seems to be the place where most of the ntfs resizing questions go, so I'll ask it here.

I have a dual-boot XP/Ubuntu (Dapper) setup on my laptop, and I'm finally ready to begin making the switch to using Ubuntu as my primary environment. This will involve moving a lot of files over from my XP partition to my Linux partition, and I don't want to eliminate XP entirely.

So the solution for me is to move all of this stuff from NTFS to Linux and resize the two partitions (shrink NTFS and expand ext3). The trouble is, I can't do it all at once because I don't have a large enough external source to back everything up.

So my plan is to do it in successive chunks: copy over as much as I can, shrink the NTFS partition using ntfsresize, expand the ext3 partition using parted, copy some more, etc.

Does this sound like a safe approach? I've done some reading on ntfsresize, and from what I can see it appears to be very safe. Will I be taking any extra risks by shrinking my NTFS partition repeatedly? Is parted safe enough to resize an ext3 partition multiple times in this way?

Thanks for the help.

---

### Post by Irony on 2006-07-29
You might want to read this;

[http://ubuntuforums.org/showthread.php?t=142503](http://ubuntuforums.org/showthread.php?t=142503)

I shrunk my windows ntfs *filesystem* but then had to shrink the ntfs *partition*, i.e. a 2 step process.

I don't think you can resize an ext3 partition, instead you will have to create another partition and copy your ubuntu installation from a live CD, e.g.;

[PHP]sudo cp -ax /mnt/hda3_Ubuntu/. /mnt/hda6_Ubuntu/.[/PHP]

---

### Post by diamond on 2006-07-29
I can't resize the NTFS partition.

When I use GParted's "Resize" command, it goes through the whole procedure and then complains that it tried to perform an operation on a busy device. This happens even when I run it off of the Live CD and ensure that no partitions from /dev/hda are mounted.

Any idea what's going on?

---

### Post by Irony on 2006-07-30
Please read the link I provided, particularly the last post of that link which I've duplicated below (you can't use GParted);
________________

Okay I've solved it. This is what I did;

First I had resized the filesystem from 60G to 15G but I pressed the wrong number as I wanted 10G, so I did the operation again using ntfs resize;

[PHP]irony@ubuntu:~$ sudo umount /dev/hda1
irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 14999994880 bytes (15000 MB)
Current device size: 61179600384 bytes (61180 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7953 MB (53.0%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3265 MB             0
Multi-Record       :      8523 MB         35500
You might resize at 7952592896 bytes or 7953 MB (freeing 7047 MB).
Please make a test run using both the -n and -s options before real resizing!
irony@ubuntu:~$ sudo ntfsresize -f -s 10G /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 14999994880 bytes (15000 MB)
Current device size: 61179600384 bytes (61180 MB)
New volume size    : 9999995392 bytes (10000 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7953 MB (53.0%)
Collecting shrinkage constrains ...
Needed relocations : 262256 (1075 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/hda1'.
You can go on to shrink the device e.g. with 'fdisk'.
IMPORTANT: When recreating the partition, make sure you
  1)  create it with the same starting disk cylinder
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you may lose your data or can't boot your computer from the disk![/PHP]

The first instruction determines what size I can shrink the filesystem to the second actually shrinks it.

I now had to shrink the partition (gparted and parted wouldn't do this despite help from ntfs tools). To do this I found [http://www.geocities.com/thekornerr/book/en_04.html](http://www.geocities.com/thekornerr/book/en_04.html) and so used fdisk to shrink the partition to slightly bigger than my shrunken filesystem;

[PHP]irony@ubuntu:~$ sudo umount /dev/hda1
irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 9999995392 bytes (10000 MB)
Current device size: 61179600384 bytes (61180 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7550 MB (75.5%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3265 MB             0
Multi-Record       :      7661 MB             9
You might resize at 7549321216 bytes or 7550 MB (freeing 2450 MB).
Please make a test run using both the -n and -s options before real resizing!
irony@ubuntu:~$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): d
Partition number (1-9): 1

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Selected partition 1
First cylinder (1-24792, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-7438, default 7438): 1217

Command (m for help): t
Partition number (1-9): 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): a
Partition number (1-9): 1

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource  busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.[/PHP]

The first instruction was simply ntfs resize again so I could look at Current volume size: 9999995392 bytes (10000 MB) and Current device size: 61179600384 bytes (61180 MB). I basically wanted to shrink the device down to just a bit bigger than volume. I thus did;

[I]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS[/I]

down to;

[I]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1217     9775521    7  HPFS/NTFS[/I]

7438 is the number of cylinders which times 8225280 bytes gives the total bytes of hda1, I therefore calculated 1217 would be about 10G. I now have about 50G of free space which I can use to shuffle the other partitions around.

---

