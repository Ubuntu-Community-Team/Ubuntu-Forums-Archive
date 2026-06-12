---
title: "Ubuntu 7.04 Graphic  Installation - Partition Question (Dual Boot w Vista)"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ZipperInt on 2007-07-06
Hi, I started to install Ubuntu yesterday but ran into a partitioning problem. 

I'm planning on dual-booting with Ubuntu and Windows Vista - I've already installed Vista, but during the graphic installation of Ubuntu from the CD, the "Guided Partition" method did not seem to be the right one to choose because it did not recognize my currently existing partitions (it only showed my hard drive as one block of space). 

I have a 250 GB SATA Hard drive that is currently partitioned the following way during my Vista installation:

75 GB - NTFS - Windows Vista installed
75 GB - NTFS - Empty (This was going to be where I put Ubuntu)
100 GB - Unformatted (I want to use this as a shared 'storage' space for music, etc.)

I'm not sure how to proceed from here. I've explored to the 'manual' partition option, but since I'm limited to 4 partitions, I don't know how to properly divide the space. When I 'create new partition' in the 100 GB free space, it gives me options that I understand (ie, selecting the amount of space, whether it is '/' or 'swap' in the pulldown menu), but I don't understand the options for the 75GB NTFS partition.

What is the best way to proceed? I assume I will need to create a '/', 'swap'  partition, and judging from other threads in these forums, a 'home' partition is what is used for sharing, but how do I deal with the pre-existing 75 GB NTFS partition, and what do I need to do to ensure that I can share files between Vista and Ubuntu on the 'home' partition?

---

### Post by Old Pink on 2007-07-06
You're going to want to make the 75GB for Ubuntu ext2 or ext3, Ubuntu won't play nice with NTFS. :) 

Best way to proceed would be booting from the LiveCD, clicking Install, choosing manual partition, reformatting the empty NTFS as ext2 and mountpointing it "/" and making yourself a 512MB (minimum) linux-swap partition. :)

---

### Post by ZipperInt on 2007-07-06
I followed your advice and changed the empty NTFS into a ext3 partition, and created a 2 GB swap partition (I have 2 GB of RAM). Both my Ubuntu and Windows systems are installed now. I'll search the doc/forums for a method of creating a shared partition that both Windows and Vista.

Thanks for the help!

---

