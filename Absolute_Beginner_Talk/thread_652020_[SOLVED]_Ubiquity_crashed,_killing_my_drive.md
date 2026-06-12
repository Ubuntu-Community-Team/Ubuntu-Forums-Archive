---
title: "[SOLVED] Ubiquity crashed, killing my drive"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by argie on 2007-12-28
I wanted to replace my Ubuntu Feisty Fawn installation with a Gutsy Gibbon installation. I wanted to install the 64-bit version. Before I start explaining what happened, I'll tell you what my drive looked like before:

/dev/sda
-/dev/sda1 - ntfs partition. My usual Windows partition. Some photos/college work I wish I hadn't lost.
-/dev/sda3 - / partition. My root partition. Nothing important on it.
-/dev/sda4 - /home partition. My home partition. _Everything_ I ever had is on this. _Everything_. I don't have much money, being a student, but $20 (all I have in Paypal) to the person who can recover this partition for me, if possible.
-/dev/sda6 (I think - My HP recovery partition.

I have installed Ubuntu before without fault on this computer. Feisty Fawn just worked. Naturally I am disappointed at losing all my data, especially my Windows drive which had nothing whatsoever to do with the partitioning. I'd like to emphasize that I moved all my data to that partition before installing, just in case something went wrong and my home directory was wiped. I'm upset that wasn't enough.

Here is what I did, the partitioning. I'll tell you what else I did if you want to know.

1. Deleted the /dev/sda3 partition.
2. Created a new partition (it became sda5). I hadn't added swap last time, so I wanted to, but if I created a primary partition on sda5 I wasn't allowed to make another (4 partitions limit, I suppose, 1 for Windows, 1 for Windows Recovery, 1 for home, and now 1 for root)
3. So I created sda5 as a logical partition (There was no option for extended partition, so I assumed that this was automatically done and that that's where sda3 went.)
4. Now I created a swap partition. Logical again. It looked okay. Everything looked okay.
5. I proceeded through the other steps with the same old settings as I'd always used on installing. 
6. Ubiquity crashes during install. I don't pay attention during the whole install because I'd gotten used to it just working, so I'd walked away. I come back to see the helpful notification in the corner telling me ubiquity had crashed.
7. A /home/ubuntu/sda3 partition has been mounted and placed on my desktop. I look at it. I can see my old root partition. It's okay. Other partitions also show in nautilus. This /home/ubuntu/sda3 partition does not unmount. Some stuff about it not being some /mtab something somewhere.
8. I restart, I don't want to take any chances partitioning a mounted drive, and I assume a restart will cause it to be unmounted.
9. The shut down goes uneventfully. I restart.
10. Load up for the shock of my life. I'm a bit numb right now.

I'd appreciate some help. All I want is for some help restoring my partition table and my data. I cannot pay for some company to do it, so if no one can help me, then thanks, it's cool, sort of. I have the whole of Saturday to attempt fixing it, and I shan't attempt any partitioning, but that's the last I can wait, college starts right after New Year, and I have stuff to do.

Oh, and one more thing: I wouldn't mind knowing what I did wrong, or if I did anything wrong at all. It would be horrible to have this happen one more time.

UPDATE: Oh my god! There's a little light shining, a tiny spark. All this time fdisk refused to report a partition and GParted reported an unallocated disk, and the Ubuntu Installer claimed the same. However, just now the result of
```
sudo fdisk -l
``` 
Output:
```
 sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8883    71352666    7  HPFS/NTFS
/dev/sda2           11314       12161     6804000    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            8884       10128    10000462+   5  Extended
/dev/sda4           10129       11313     9518512+  83  Linux

Partition table entries are not in disk order

```

This must mean something good! The data is still there. I just have to repair the partition. Someone must know! Help would be appreciated. I'll also change the title, shouldn't have said ubiquity but that's what that crashed program notification said.

Update:
[quote=Wander_w]argie: I'd make a backup of your partition table; you should use dd for that like: dd if=/dev/hda of=~/my_partition_table_backup count=123   Lookup the correct way to do this[/quote]
So I've made a backup of my partition table using the following command.
```
sudo dd if=/dev/sda of=~/sda-mbr.bin bs=512 count=1
```
I found it here: [http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html](http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html)

Similar problem:
[http://ubuntuforums.org/showthread.php?t=353658](http://ubuntuforums.org/showthread.php?t=353658) (with solution, sort of)

HURRAH! My stuff is still safe, thank the gods! testdisk to the rescue. I love that software. I just love it. It didn't just correct the partition table, it did magic on it so that an extended partition appeared where I hadn't put it but where it would be perfect for it to be. A donation is in order.

---

### Post by blueridgedog on 2007-12-28
> **argie said:**
> I 
1. Deleted the /dev/sda3 partition.
2. Created a new partition (it became sda5). I hadn't added swap last time, so I wanted to, but if I created a primary partition on sda5 I wasn't allowed to make another (4 partitions limit, I suppose, 1 for Windows, 1 for Windows Recovery, 1 for home, and now 1 for root)



I think this is the core or start of your problem, you created a logical partition (sda5) but it needs to reside in an extended partition, which must be one of your four primary partitions.

I suspect that whereas you you think you created sda5, you may actually have made a new sda3 at an extended partion, which then did not have any logical partitions in it.

If at all possible I try and stick to primary partitions in working with dual/multi boot setups and also try to stick to them when talking others through problems.

---

### Post by argie on 2007-12-28
> **blueridgedog said:**
> I think this is the core or start of your problem, you created a logical partition (sda5) but it needs to reside in an extended partition, which must be one of your four primary partitions.

I suspect that whereas you you think you created sda5, you may actually have made a new sda3 at an extended partion, which then did not have any logical partitions in it.

If at all possible I try and stick to primary partitions in working with dual/multi boot setups and also try to stick to them when talking others through problems.

I see. That seems likely.. However, the reason that happened is because when I deleted the old sda3 and attempted to make an extended partition, the New Partition dialog box showed me only two radio buttons at the top: Primary or Logical. If someone would check this so as to confirm that it wasn't just me being foolish, then perhaps we should report that as a bug. Perhaps it's just me but I'm pretty sure a program could ensure that such a mistake wouldn't happen.

I would have used only primary partitions. In fact, that's what I had earlier, but that wouldn't allow me a separate /home partition *and* a swap partition. This time I wanted my swap :)

Thanks.

---

### Post by blueridgedog on 2007-12-28
I will mock it up as well.  I am an "older" Linux guy and have never (until my recent conversion to Ubuntu) used anything other than fdisk to manage disks.  I bet the problem is as you describe...

---

