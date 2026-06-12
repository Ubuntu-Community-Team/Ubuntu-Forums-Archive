---
title: "Differences between bootsector and its backup."
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-28
When I partitioned my 2 HDs in a very multi partition way.  The live Draker 6.06 CD couldn't handle it all at the same time when I finished the process by formating all my new partitions.
Therefore I had to do it in 2 procedures, I cut out the major part like I wanted it to and then I went back after reformating to cut the other section.
This separated process seem to have confused Grub.  OR it has something to do with that I tried to do all this above in one whole swoop earlier and the installation froze on me so.....3 times the confusion.

This is what it says on the black screen/white text startup part:
> 
There are differences between bootsector and its backup.
Differences: (offset: original/backup)
{followed by a bunch of HEX like numbers and stuff}

Does anyone know how to heal my Grub? :-k

---

### Post by jingo811 on 2006-11-28
Since menu.lst wasn't the real problem I deleted it to make the thread easier to view.

---

### Post by anaconda on 2006-11-28
The menu.lst -file doesn't have anything to do with your problem. The error comes before Grub stage2 is loaded. stage1 is in mbr and stage2 is in the /boot.. stage2 reads the menu.lst

I am no expert, but it sounds like you have a problem with your mbr or partition table (which is in the end of mbr).

You can reinstall grub to ensure that the mbr(exluding partition table) is correct. Search the forums with 
restoring grub after installing windows
or just
restoring grub 

And if the problem is with partition table (which is what I think) can you post the output of:
sudo sfdisk -l
(or sudo fdisk -l if you dont have sfdisk installed)
so I or someone else can comment if it is OK!

Found a link that might be of interest:
[http://ubuntuforums.org/showthread.php?t=32531](http://ubuntuforums.org/showthread.php?t=32531)

---

### Post by steve.horsley on 2006-11-28
Are you sure there's a problem? I get a message about a difference between the bootsector and its backup. I just ignore it. Everything works fine.

---

### Post by jingo811 on 2006-11-28
...

---

### Post by jingo811 on 2006-11-28
So I tried anacondas 1st advice but I didn't know what to do halfways through so I need some guidance before proceeding.

**1. sudo grub** - OK.
**2. find /boot/grub/stage1** - OK it shows (hd01,2) and (hd1,1).
**3. root (hd?,?)** - Both (hd01,2) and (hd1,1) shows...
...Filesystem typ is ext2fs partition type 0x83.....
...Which should I pick?
[B]
4. setup(hd?)[/B] - Don't know which hd? to insert!
**5. quit** - Have not come this far!




my "restore grub" tutorial source:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by jingo811 on 2006-11-28
I went ahead to do the sfdisk -l in case you needed that anyway.

> mike@mike-shark:~$ sudo sfdisk -l
Password:

Disk /dev/hda: 79656 cylinders, 16 heads, 63 sectors/track
[COLOR="Red"]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.[/COLOR]
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 79656/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

  ** Device Boot Start     End   #cyls    #blocks   Id  System**
/dev/hda1   *      0+   1274    1275-  10241406    c  W95 FAT32 (LBA)
/dev/hda2       1275    4652    3378   27133785    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3       4653    4997     345    2771212+  83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       1275+   1465     191-   1534176    b  W95 FAT32
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/hda6       1466+   4652    3187-  25599546    b  W95 FAT32
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)

Disk /dev/hdb: 79656 cylinders, 16 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 79656/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

  ** Device Boot Start     End   #cyls    #blocks   Id  System**
/dev/hdb1          0+    126     127-   1020096    b  W95 FAT32
/dev/hdb2        127    1441    1315   10562737+  83  Linux
/dev/hdb3       1442    1569     128    1028160   82  Linux swap / Solaris
/dev/hdb4          0       -       0          0    0  Empty

Disk /dev/sda: 1018 cylinders, 4 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/8/32 (instead of 1018/4/62).
For this listing I'll assume that geometry.
Units = cylinders of 131072 bytes, blocks of 1024 bytes, counting from 0

  ** Device Boot Start     End   #cyls    #blocks   Id  System**
/dev/sda1   *      0+    986-    987-    126217    6  FAT16
                end: (c,h,s) expected (986,1,18**'**) found (1023,7,32)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
mike@mike-shark:~$

What should I do now???

---

### Post by jingo811 on 2006-11-29
Never mind this seemed to do the trick for hda1 - Fat32

> 1.**sudo dosfsck -ar /dev/hda1**
or
sudo fsck -V -r /dev/hda1

2.**original -> backup**


If Windows partition was NTFS I read that using Windows Recovery and then use **fixboot** or something would be a better solution than above...if you have a complaining NTFS filesystem.

---

