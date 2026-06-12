---
title: "Partitioning gone wrong"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by KentS on 2007-12-19
I tried to partition my hd. During the process an error occurred (I didn't get any details) and my entire hd shows up as unallocated. When I start gparted it says something about illegal(?) partition table. 
Windows still works, and shows my Windows partition and Recovery partition. Ubuntu starts to boot, but stops when it doesn't find all partitions. 
What should I do?
Will a system recovery handle the ext3 partitions, so that I get a totally clean system?
Do I have other options?

---

### Post by hyper_ch on 2007-12-19
do you have vista installed there?

---

### Post by KentS on 2007-12-19
No, XP.

---

### Post by hyper_ch on 2007-12-19
then I'd recommend you grab a copy of partition magic, check your partitions and stuff in XP.... create the parttiions you want for linux and then install linux into those.

---

### Post by KentS on 2007-12-19
Are there any other partition managers that would work? I'd prefer not having to buy partition magic.

---

### Post by hyper_ch on 2007-12-19
I dunno...  you can try the gparted live-cd

---

### Post by KentS on 2007-12-19
Unfortunately, that's where my hd shows up as unallocated.

Do you know if a system/PC recovery would work? I don't have anything I can't loose on my PC.

---

### Post by Sef on 2007-12-19
> Unfortunately, that's where my hd shows up as unallocated.

Do you know if a system/PC recovery would work? I don't have anything I can't loose on my PC.

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by bumanie on 2007-12-19
Is it possible to send a screenshot of what g-parted shows? This may or may not be helpful, but it is worth a try.

---

### Post by gkaufman on 2007-12-19
I had the same issue - be sure that you've defragged your drive a few times. google for dirms - it was on an earlier ubcd, but not the latest one. I found an older freeware copy (it's now commercial). dirms works really well - defrags and moves all of the files to the front of the drive. 

After I did that, gparted gave me a second option about unallocated space, and recognized the size of my existing win partition.

---

### Post by rob.webinator on 2007-12-19
I'm posting here because I think I have a related problem.

I have a dual boot IBM/Lenovo T61P with WinXP and Gusty with the following partition table:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2580    20721928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3222       11576    67111537+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           11577       12161     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5            3223        6406    25572645    b  W95 FAT32
/dev/sda6            6406        7297     7164958+  83  Linux
/dev/sda7            7298        7552     2048256   83  Linux
/dev/sda8            7553       11385    30788541   83  Linux
/dev/sda9           11386       11576     1534176   82  Linux swap / Solaris

However, GParted just says "Unallocated" for the entire physical device (attachment).

I ran testdisk (more attachments) and saw the expected table with these Warnings:
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Warning: Incorrect number of heads/cylinder 240 (FAT) != 255 (HD)
Warning: the current number of heads per cylinder is 255 but the correct value may be 8.

I desperately need to resize my FAT32 partition to gain more Gutsy OS (/) and ext3 data space.

Any ideas?

R

---

### Post by hyper_ch on 2007-12-19
you could try that:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by KentS on 2007-12-19
> **Sef said:**
> Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

Thank you. That worked.

I won't mark this thread as solved yet, since others apparently have similar problems.

---

### Post by psusi on 2007-12-19
Hrm... strange... rob, it looks like sda5 and sda6 might be slightly overlapping.  Could you post the output of sudo fdisk -lu?

---

### Post by rob.webinator on 2007-12-19
Wicked.  Good call psusi, sda5 and sda6 are indeed overlapping.  How to fix?

Is it also odd that sda2 is a "W95 Ext'd (LBA)" extended partition which contains partitions 6,7,8 and 9 which are linux intended?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41443919    20721928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        51745365   185968439    67111537+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       185976000   195365519     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5        51761430   102906719    25572645    b  W95 FAT32
/dev/sda6       102896388   117226304     7164958+  83  Linux
/dev/sda7       117226368   121322879     2048256   83  Linux
/dev/sda8       121322943   182900024    30788541   83  Linux
/dev/sda9       182900088   185968439     1534176   82  Linux swap / Solaris

---

### Post by psusi on 2007-12-19
I'd say get what you can off sda5, then blow it away and do a fsck -f /dev/sda6.

---

### Post by rob.webinator on 2007-12-21
That worked like a dream, thanks.

---

