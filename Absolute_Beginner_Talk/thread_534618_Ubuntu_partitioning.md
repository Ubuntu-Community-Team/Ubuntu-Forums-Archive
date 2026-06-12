---
title: "Ubuntu partitioning"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
I have a 160gig harddrive that I want to partition into 2 partitions. One drive as the OS and the other as the DATA drive (for storing my documents etc).

I'm using the manual partitioning option in Ubuntu.
1) The partition I'm installing Linux on, should I make it a Linux partition? (there is diff types of linux partitions, which one is best)
2) Should I leave the "data" partition as NTFS or will I benefit from creating it as a Linux partition?
3) Also, do I need a Linux swap partition? What is a swap partition?

---

### Post by henriette_holm on 2007-08-25
Hi.
You need the following partitions:

partition1: / (root - this should be ext3)
partition2: /home (ext3 - use this for data)
partition3: swap (2 * the amount of ram as a rule of thump)

Now, this is sort of the "basic" setup. Do you need to share data between two OS?

Also, take a look at this: [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

/Henriette

---

### Post by Daveth on 2007-08-25
if you are  sharing data with windows then you need your data partition to be FAT32 rather than NTFS, the  write ability to which is still rather "edgy". If this is just an Ubuntu box then ext3 all the way!

Don't forget that with Gparted your mount point for your home partition will, of course, be /home.

---

### Post by kellemes on 2007-08-25
> **Daveth said:**
> if you are  sharing data with windows then you need your data partition to be FAT32 rather than NTFS, the  write ability to which is still rather "edgy". If this is just an Ubuntu box then ext3 all the way!

Don't forget that with Gparted your mount point for your home partition will, of course, be /home.


For sharing you better use ext3
The ext3-support on Windows is very stable and provides you with all the nice features of ext3.

---

### Post by Daveth on 2007-08-25
I was not aware of that - useful to know- thanks

---

