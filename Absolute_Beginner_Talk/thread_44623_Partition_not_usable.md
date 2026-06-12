---
title: "Partition not usable"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Moosferatu on 2005-06-27
I partioned my hard drive using QTParted on the SystemRescueCD today.  I resized the NTFS partition, created a FAT32 partition, and left some free space for Ubuntu.  When I go to install Ubuntu it says that the free space is unusable.  Could it be related to the fact that there were already two other partitions on the drive when I got it from Dell?

hda1: 58MB FAT16 (some Dell thing)
hda2: 34GB NTFS (Windows)
hda4: 26GB FAT32 (shared storage)
hda-1: 10GB Free Space
hda3: 3GB FAT32 (Some Dell thing again.  I think it's some system restore thing)

Anyone have any ideas?

---

### Post by mohaham on 2005-06-27
This has nothing to do with the 2 DELL partitions. I have them on my laptop too.
why dont u try creating 2 partitions(one for root and the other for swap) in the freespace using SystemRescueCD.

---

### Post by Moosferatu on 2005-06-27
For some reason it won't let me do anything to that partition in QTParted either.  It only lets me look at its properties.

---

### Post by Moosferatu on 2005-06-27
I got it now.  Because of the Dell partitions I had reached the limit of primary partitions so I had to delete one of my existing partitions and recreate it as logical.

---

