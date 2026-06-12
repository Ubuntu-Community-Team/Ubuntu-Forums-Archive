---
title: "How to Read/Write on Mac Formatted External Hard Drive in Ubuntu"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by amerikanYippie on 2009-06-12
Hi, I'm somewhat new to Linux OS's and have a question regarding external hard drives.

My main computer is a MacBook Pro, running OS X 10.5.1.  As I understand it, this means that the Maxtor OneTouch 4 (250GB, I think) External Hard Drive I use with my Mac is HFS+ partitioned.  Correct?

I want to be able to read and write to this external HD on my Dell Inspiron 600m, which is now running Ubuntu 9.04 (Jaunty Jackalope), without losing any of the files that are on it now, and without losing the ability to use it on my Mac.

I've read a few solutions using GParted, but those were mostly for older versions of Ubuntu, and somewhere else I read that 9.04 can read HFS+.  Should I just be able to plug it in and use it in either computer?  I really can't lose any of the files on it, so I don't want to do anything I'm not 100% sure will work.

Thanks!

---

### Post by evilempire on 2009-06-13
The first thing is to find out what format you ahve on the external. If it works on the Mac - it's either HFS+ (mac) or more likely Fat32. Drive manufacturers like to use fat32 on stuff because it works on practically anything. Plug the drive into the mac and open Disk Utility (found in /applications/utilities) - it will tell you what type of format you have. 


If it's fat32 - you can read and write that on a linux machine. The main drawback to fat 32 is that you cant have any files larger than 2GB. It can also get corrupted easier than some of the more modern filesystems. 

IF it's HFS+, Ubuntu can read the drive just fine but won't write to it by default. 

Also you say you are running 10.5.1 - you should download and run the 10.5.7 update, there are hundreds of fixes in it...  It's a large update though ~600 MB i think.

---

### Post by mikedep333 on 2009-06-14
I've read on numerous occasions that you can make your external HFS+ partition/drive work with Ubuntu by disabling journaling on it from the Mac OS X disk utility.

---

### Post by cyberdork33 on 2009-06-15
> **evilempire said:**
> If it's fat32 - you can read and write that on a linux machine. The main drawback to fat 32 is that you cant have any files larger than 2GB. It can also get corrupted easier than some of the more modern filesystems. 
that's actually 4GB.... but yes FAT32 is the most compatible filesystem. NTFS is also supported on both via FUSE.

> **mikedep333 said:**
> I've read on numerous occasions that you can make your external HFS+ partition/drive work with Ubuntu by disabling journaling on it from the Mac OS X disk utility.
Disabling journaling on a filesystem that supports it is really not a good option. It will work, but without journaling, the HFS+ filesystem might as well be FAT32 or NTFS.

---

