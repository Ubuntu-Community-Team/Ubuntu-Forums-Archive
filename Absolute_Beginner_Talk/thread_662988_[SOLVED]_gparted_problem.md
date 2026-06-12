---
title: "[SOLVED] gparted problem"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2008-01-09
I'm dual booting Ubuntu and XP.  I have a partition for each os plus a swap for both, and one partition where I put my data.  I realized that I want to use Ubuntu more but I was running out of space so I decided to reduce my windows partition and extend my ubuntu one.  I reduced the windows partition using acronis disk manager.  And took the new partition and formatted it to ext 3.  I was hoping to be able to get it to merge with my ubuntu partition.  I thought it would probably be best if I were to do that with gparted.

When I start gparted (as root) I see my partiton, but when I click on refresh devices I get this error.

root@whitethorn-laptop:/home/whitethorn# gparted
======================
libparted : 1.7.1
======================
Can't have overlapping partitions.
Can't have overlapping partitions.
Segmentation fault (core dumped)

Neone know what I should do?  I can mount the new ext3 partition.

---

### Post by thelatinist on 2008-01-09
Please post the results of

```
sudo fdisk -l
```

---

### Post by whitethorn on 2008-01-09
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         849     6819561    7  HPFS/NTFS
/dev/sda2             850        7296    51785527+   5  Extended
/dev/sda3            1276        2040     6144862+  83  Linux
/dev/sda5             850        1275     3421813+  83  Linux
/dev/sda6            2041        2193     1228941    7  HPFS/NTFS
/dev/sda7            2347        7296    39760843+   7  HPFS/NTFS
/dev/sda8            2194        2346     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc61fa308

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32
/dev/sdb2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 4060 MB, 4060086272 bytes
229 heads, 32 sectors/track, 1082 cylinders
Units = cylinders of 7328 * 512 = 3751936 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1083     3964912    c  W95 FAT32 (LBA)

---

### Post by logos34 on 2008-01-09
So it looks like you shrank sda6 and created a new ext3 with Acronis, sda3--is that correct?  If so, acronis screwed up because logical partitions start at 5.  No wonder Gparted is having problems.  If that's the case,  find a way to delete the ext3 you just created.  Then use Gparted on the ubuntu live cd to expand sda5 into empty space. (correct me if I got the details wrong).

---

### Post by whitethorn on 2008-01-09
"Device Boot Start End Blocks Id System
/dev/sda1 * 1 849 6819561 7 HPFS/NTFS
/dev/sda2 850 7296 51785527+ 5 Extended
/dev/sda3 1276 2040 6144862+ 83 Linux
/dev/sda5 850 1275 3421813+ 83 Linux
/dev/sda6 2041 2193 1228941 7 HPFS/NTFS
/dev/sda7 2347 7296 39760843+ 7 HPFS/NTFS
/dev/sda8 2194 2346 1228941 82 Linux swap / Solaris"


"So it looks like you shrank sda6 and created a new ext3 with Acronis, sda3--is that correct? If so, acronis screwed up because logical partitions start at 5. No wonder Gparted is having problems. If that's the case, find a way to delete the ext3 you just created. Then use Gparted on the ubuntu live cd to expand sda5 into empty space. (correct me if I got the details wrong)."

No not quite, acronis shrunk the sad1 (ntfs), and created the sda5, sda3 is the root,  I won't be able to fix it using the CD for a couple days, I lent it to a friend.  Nething else I can try?

---

### Post by thelatinist on 2008-01-09
The think the problem is with your second hard drive (/dev/sdb).  It appears you have two partitions on that drive, the second one is a tiny bootable partition which is empty.  The problem is that this partition "overlaps" the first partition (Both of them start at block 1).  I don't know how this happened, but it should be solvable simply by deleting /dev/sdb through Gparted.  I suggest you boot into the Live CD and try deleting it from there.  Give that a try and see if that fixes your error message.

As for what you are originally trying to do, please note that you can't "merge" partitions, if you mean by that combine two existing partitions into one. You will only be able to delete one of them and resize the other to fill the space freed.  If you have data on one of the partitions, you will have to back up the partition you are going to delete so you can copy it to the resized partition when it is done.

---

### Post by whitethorn on 2008-01-09
Umm how can I backup the data on my drive?  I'm trying to resize the partition which serves as both my root and home partition.

---

### Post by thelatinist on 2008-01-09
> **whitethorn said:**
> Umm how can I backup the data on my drive?  I'm trying to resize the partition which serves as both my root and home partition.

Have you saved anything on /dev/sda5?  If not, just delete that partition and resize /dev/sda3 to the left using a Live CD (you can't resize your root partition while running Linux from it).  Please be aware that this will take several hours...maybe as many as twelve or fourteen.  Resizing to the left takes a long time, during which you cannot use your computer.  Please also be aware that if the power goes out or you turn off your computer, you will lose everything in both partitions.  This is why it is always recommended to backup before messing with partitions.

If you have saved data on /dev/sda5, you will have to backup the stuff you've saved there before you delete it.  Save it to another disk, burn it to DVDs, etc.  There is no other way to get one large partition from two smaller ones...partitions simply cannot be "merged."

---

### Post by whitethorn on 2008-01-09
I didn't save anything to the partition I had acronis format it as well.  Ok I'll go delete it, and then resizing the sda3 partition.

---

