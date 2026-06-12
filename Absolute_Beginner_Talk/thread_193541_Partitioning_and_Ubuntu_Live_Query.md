---
title: "Partitioning and Ubuntu Live Query"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Liehann on 2006-06-10
Hi,

I'm new to Linux, especially installing and configuring and am hoping someone can give me some help with the following. I have version 5.10.

1. Ubuntu Live SATA HDD and IDE DVD Drive

I have a Gigabyte GA-81955X Royal motherboard. In the BIOS there is a setting  On-Chip SATA Mode. Mine was set to Combined which is described as "Set On-Chip SATA mode to Combined, you can use up to 4 HDDs on the motherboard; 2 for SATA and the other for PATA IDE." When this mode is selected Ubuntu does not seem to be able to recognize my cdrom drive (actually DVD but the Live startup / installation program refers to it as a cdrom drive). I am prompted to either use a driver on a floppy disk or select from a list of options. I've tried most of the options and none of them work. 

If I select Disabled for this BIOS settings Ubuntu Live boots fine but my SATA HDD is disabled and is not available under devices for mounting.

The reason I tried this setting is I noticed another post where someone did something similar but I don't think they had a SATA HDD.

So I would appreciate some help with getting Ubuntu Live to correctly recognize the IDE dvd drive when the SATA hard drive is enabled. Also I realize that this post is probably better suited to the one of the technical forums but the second part of the post is more beginner.

2. More General Query Regarding Co-Existance of Windows and Linux

What I would like to do is run a dual boot system with three partitions.
1. Windows OS and Apps
2. Linux OS and Apps
3. Data Files - ie. Mp3s and Videos, stuff that would be used by both Windows and Linux.

My system is currently a Windows system and I would like to migrate to the desired setup without having to re-install Windows. I currently only have 1 partition with all data and Windows OS.

This is also the reason I am running the Live CD. I want to check out Ubuntu without sacrificing my current installation.

In advance thanks to anyone who takes the time to read this post and reply.

Regards,
Liehann

Edit
--------
The post I mentioned is: [http://www.ubuntuforums.org/showthread.php?t=152180]("http://www.ubuntuforums.org/showthread.php?t=152180"). Here he removes SATA drives and uses and IDE drive via caddy so does not require interoperability.

---

### Post by Dr. Nick on 2006-06-10
I dont use sata so cant help the first part. But the 2nd I can.

You can resize your windows partition to allow room for ubuntu. If you want to share data between the 2 It would be best to make a fat32 partition to put the data on since both os's can read/write to fat32, While linux can only read ntfs but not write,

You can get a program for windows to read ext2 drives if you choose to.
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm#Download)


To make things easier leave windows as the first artition and put linux on the end of the drive, I believe the live cd install has the tools needed to resize it all.

---

