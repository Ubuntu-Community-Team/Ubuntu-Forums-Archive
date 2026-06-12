---
title: "partitioning Hard Drive for Xubuntu"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Five_Iron_OBrien on 2007-10-15
I have an Acer TravelMate 2420 with two hard drives both 20 gigs each.  I have Windows XP on the C drive. I'd like to install a dual boot with Xubuntu 6.06.  I'm kind of confused with how to partition it so that I only use drive D.

Thanks!

---

### Post by Five_Iron_OBrien on 2007-10-15
not to be impatient but *bump*

---

### Post by bashveank on 2007-10-15
Just don't touch the partition on drive C.

?

---

### Post by Keith_Burton on 2007-10-15
Your "d:" drive is "/dev/hdb" to Linux. ("c:" is /dev/hda).

I personally like 3 partitions:
/dev/hdb1, 3GB, as your root partition (mount point "/").
/dev/hdb2, 512MB to 2GB, equal to your RAM, as a swap partition.
/dev/hdb3, the rest of the disk, mount point "/home". 

There are lots of ways to do it, but if you keep your /home partition separate, you can upgrade the OS without it overwriting any of your personal files.

---

### Post by Five_Iron_OBrien on 2007-10-15
so is hda1 where windows is on?

---

### Post by por100pre1 on 2007-10-15
> **Five_Iron_OBrien said:**
> so is hda1 where windows is on?

Yes, the previous poster meant to make 3 partitions on the second hard disk drive, we are assuming the first hard disk drive (in Linux it is hda) is the drive C.

---

