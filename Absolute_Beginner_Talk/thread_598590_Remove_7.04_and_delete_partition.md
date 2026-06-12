---
title: "Remove 7.04 and delete partition?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by squiggly on 2007-10-31
Hello all, I hope I can find an answer here.

I installed 7.04 a few months ago but didn't have the time to play with it much. When 7.1 came out, I tried to get 7.04 to update to 7.1, but it errored. So I burned a new 7.1 disc and installed it, hoping it would install over 7.04. It did not.

Instead now I have 5 partitions on my drive as follows:
- common FAT32 partition to house data files to be shared by Ubuntu and Windows XP (approx 100gb)
- a partition with 7.04 (approx 36gb)
- a partition with 7.04 cache (small)
- a partition with 7.1 (approx 34gb)
- a partition with 7.1 cache (small)

How can I remove 7.04 and delete their partitions in order to increase the 7.1 partition size? Is this even possible?

Thanks for any hints!
squiggly

---

### Post by ukripper on 2007-10-31
Can you post output of the follwoign commands :
```
sudo fdisk -l
```

```
blkid
```

---

### Post by squiggly on 2007-11-03
```
sudo fdisk -l
```
Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8dbc8db

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd658ef95

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9777    78533721    7  HPFS/NTFS
/dev/hdb2            9778       14557    38395350   83  Linux
/dev/hdb3           18891       19457     4554427+   5  Extended
/dev/hdb4   *       14558       18890    34804822+  83  Linux
/dev/hdb5           19083       19457     3012156   82  Linux swap / Solaris
/dev/hdb6           18891       19082     1542177   82  Linux swap / Solaris

Partition table entries are not in disk order


```
blkid
```[/QUOTE]
/dev/hda1: UUID="386495DC64959CE6" TYPE="ntfs" 
/dev/hdb1: UUID="8ACC80ECCC80D43B" LABEL="Common Data" TYPE="ntfs" 
/dev/hdb2: UUID="917803e4-1b9b-493d-b5fe-2865a7d6f9a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb4: UUID="09a2c480-f80d-4b48-bfdd-7d46a26d036a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="ea8b057e-c09a-4018-bb3d-61bad211a8bc" TYPE="swap" 
/dev/hdb6: UUID="571b3ba3-7327-4348-b392-ad5816d33e0e" TYPE="swap" 


Oops... I mispoke earlier. The common data file is NTFS, not FAT32.

Thanks for the help!
Chris

---

### Post by ukripper on 2007-11-03
Boot from Live CD and run program called GPARTED and find 7.04 partitions and delete it from there. Make sure you take backup your system or probably use clonezilla [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)  to clone your disk.


From above output i am unable to determine on which one 7.04 is installed.

---

### Post by mdpalow on 2007-11-03
Very possible and very easy... :)

Use Synaptic Package Manager to download " gparted," which will allow you to look at/manage your partitions.

After opening up gparted from your menu option (Partition Editor), find the partition(s) you want to remove and delete them. After deleting, click on the 7.10 partition and grab -with your mouse- the right side (it's represented with a box) and DRAG it to the right until it slides as far as it can go. This is called GROWing your partition to use all that you just made available by deleting the others. 

I just did this yesterday and the data on that drive was NOT affected or deleted, so you should be fine.

If all else fails, you could just reinstall 7.10 and do a MANUAL partition when it comes up during install. Here you would click on each partition and delete it. Then create three new/more:

/                : 20 gigs / EXT3 file format
/home        : remaining hard drive space minus 3 gigs / EXT3 file format
/swap        :3 gigs

Good luck,

---

### Post by yogo on 2007-11-03
I

---

