---
title: "Limit on Partitions?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by openmind on 2006-04-04
Noob Question, is there a limit on the amount of partitions on a hard drive?
 
I'm planning on redoing my disk for Dapper, this is the plan;
 
XP (NTFS)
Shared (FAT)
/boot
/ (ext3)
/home (ext3)
linux-swap
 
6 partitions, will there be any probs?
 
Thanks.

---

### Post by Sef on 2006-04-04
You can only have 4 primary partitions.  The rest have to be logical partitions.  And what you have looks fine.

---

### Post by TLE on 2006-04-04
Nope ! Shouldn't be a problem, in fact as I understand it you can make a seperate partition for each one of the folders in the root directory if you wish. By the way, in my opinion fat32 is not the best solution for a shared partition, I just use a ext3 partition along with a ext2 driver for XP, I can post a link later if you are interessted.

---

### Post by Sef on 2006-04-04
FAT32 or ext 2 for a shared file.  It really boils down to your preference.  Both will work fine.

---

### Post by openmind on 2006-04-04
Sef, forgive my ignorance, I've set up partitions using qtparted before but how do I set up 'logical' partitions, and how would I know the difference? Which ones would be logical?
 
Thanks.

---

### Post by TLE on 2006-04-04
Yeah I supposed you are right I was just thinking that fat32 is an old system and so I have more faith in acces permission control and general reliability with ext3. BTW thanks for clearifying that about primary and secondary partition I think I went in over my head there ;)

---

### Post by Sef on 2006-04-04
[QUOTE]Sef, forgive my ignorance, I've set up partitions using qtparted before but how do I set up 'logical' partitions, and how would I know the difference? Which ones would be logical?[QUOTE]

When you set up the partitions, it gives u a choice of primary or logical.  I made the first 4 of mine  primary (FAT32, root, home, and forget the other one at the moment) and the last one logical (swap for me.)

---

### Post by AndyCooll on 2006-04-04
Due to the limitation of primary partitions as mentioned above if you need more than four, then  the onluy way to do this is to add a logical partition. You can only have one of these, but this in itself can be sub-divided, and I don't think there's any limit on how many sub-divided partitions you can have.

I usually have a boot primary partitions, swap primary, main operating system primary, and then additional OS's on separate partitions within the logical partition 

:cool:

---

### Post by pommattski on 2006-04-04
You need to have at least 1 **primary** partition (with a maximum of 4).
Instead of one of the **primary** partitions, you can choose to create an **extended** partition. Then you can create as many **logical** partitions on the **extended** partition as you wish.

---

### Post by steve.horsley on 2006-04-04
The disk can have up to 4 **primary** partitions.
One of those primary partitions can be an **extended** partition, which is a partition that contains **logical** partitions (almost any number). 

The primary partitions are always partition numbers 1, 2, 3, 4.
Logical partitions number from 5 upwards, and can only exist inside an extended (primary) partition. See the printout below. You will see by looking at the start and end cylinder numbers that the partition numbers above 4 are all inside the extended partition number 3.


```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           9       72261   de  Dell Utility
/dev/hda2   *          10        1925    15390270    7  HPFS/NTFS
/dev/hda3            1926        4864    23607517+   5  Extended
/dev/hda5            1926        2654     5855661   83  Linux
/dev/hda6            2655        3383     5855661   83  Linux
/dev/hda7            3384        3505      979933+  82  Linux swap / Solaris
/dev/hda8            3506        4234     5855661   83  Linux
/dev/hda9            4235        4864     5060443+   b  W95 FAT32


```

---

