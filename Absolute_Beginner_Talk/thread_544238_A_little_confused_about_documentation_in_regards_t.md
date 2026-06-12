---
title: "A little confused about documentation in regards to hard drive formats and read/write"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by palian on 2007-09-06
**Background:** I recently built a computer with a 500g hard drive and made 40g NTFS partition for XP for games and other Windows friendly programs. Another partition is for Ubuntu. I have files that I want both OS to access. I want to have the files on a partition separate from either OS in case the OS comes crashing down (a bigger concern with XP I am assuming). If possible I want to avoid creating two partitions with duplicate files just so both OS can read/write the files.

**Now:** I was hoping there maybe some tool or neutral hard drive format that would allow XP and Ubuntu have read/write access to the partition intend to be a repository. Is there anything that comes to anyone's mind? 

**The Main Problem:** I have read some of the documentation on Ubuntu.org regarding  formating and read/write access but [a bottom section of this document]("https://help.ubuntu.com/community/WindowsDualBoot") seems to contradict [this document]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite"). So can Ubuntu read/write files **safely ** on a NTFS partition? Further more, is this the best way to way to go about granting access to files to both OS yet keeping the files separated from either one with out redundancy? Or is there something else one might recommend?

---

### Post by alienexplorers on 2007-09-06
Why not just create a FAT partition that both ubuntu and windows can read and write to.  This is what I did instead of playing with NTFS-3g.

---

### Post by hyper_ch on 2007-09-06
You have different options:

(1) FAT32
Both system can read/write Fat32 natively and nothing else is required... however Fat32 is ancient, supports only files up to 4 GB, has no journaling, ....

(2) NTFS
In Ubunt you'll need to have ntfs-3g installed... I've never tried it myself but meanwhile it seems to run ok... however NTFS is proprietary and there's still guesswork on it and if it fails, it fails big-time... as said, haven't read of any failure yet

(3) Ext2/3
Ext3 is the most recommended filesystem under linux - especially if you don't really know what other options you have... if you konw, you may want to use other fs like Reiser... it depends on what you want to do...
There are Ext2/3 drivers available for windows. As Ext2/3 is open source I tend to think the drivers will be less problematic on windows than ntfs-3g drivers on linux. You can get them here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

I'd go for Ext2/3 if I was in your situation.

---

### Post by Sef on 2007-09-06
> Why not just create a FAT partition that both ubuntu and windows can read and write to. This is what I did instead of playing with NTFS-3g.

Use [ext2/3]("http://www.fs-driver.org/") instead.  It is more stable than FAT32

---

### Post by aquavitae on 2007-09-06
> **palian said:**
> I was hoping there maybe some tool or neutral hard drive format that would allow XP and Ubuntu have read/write access to the partition intend to be a repository. Is there anything that comes to anyone's mind?
You have two options: NTFS or ext3.  I don't consider FAT a good option because of all the limitations in the format.

> 
I have read some of the documentation on Ubuntu.org regarding  formating and read/write access but [a bottom section of this document]("https://help.ubuntu.com/community/WindowsDualBoot") seems to contradict [this document]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite"). So can Ubuntu read/write files **safely ** on a NTFS partition?Yes.  The first document is incorrect (or may just be old).  The NTFS 3G driver will write safely to NTFS, but its a fairly new piece of software (but stable) so old docs don't refer to it.
> 
Further more, is this the best way to way to go about granting access to files to both OS yet keeping the files separated from either one with out redundancy? Or is there something else one might recommend?
As I said, the other option is ext3, a linux file system.  Ext3 is, in my opinion, a much better file system than NTFS - you don't have to defrag it, it is stable, it has better permission support, and there is a windows driver for it.  I'll have to look for it though and I'll post when I find it.  But basically the answer is you can share files on either NTFS or ext3.  I suggest you google a bit and see the various pros and cons of each.

---

### Post by alienexplorers on 2007-09-06
I use FAT32 because it requires no un-needed programs for ubuntu and windows to read and write to it.  If I use etc2/3 I need a special program in windows to read and write to the partition.  If I use NTFS Ubuntu needs NTFS-3g to read and write to it.  So FAT32 was the simplest way to go.

---

### Post by aquavitae on 2007-09-06
NTFS-3G is just a kernel module.  So is vfat which is used to access fat drives.  Its not even really a program, just a little bit of code which the kernel uses to read and write to a specific file system.  In fact, I think the onlly reason it isn't included in the linux kernel by default is that its so new.

---

### Post by palian on 2007-09-06
Thanks to everyone who replied, I didn't expect such quick responses.

> (1) FAT32
Both system can read/write Fat32 natively and nothing else is required... however Fat32 is ancient, supports only files up to 4 GB, has no journaling, ....


I forgot to add in my OP that I had considered FAT32 but decide to see if I could find something else.


> **aquavitae said:**
> As I said, the other option is ext3, a Linux file system.  Ext3 is, in my opinion, a much better file system than NTFS - you don't have to defrag it, it is stable, it has better permission support, and there is a windows driver for it.  I'll have to look for it though and I'll post when I find it.  But basically the answer is you can share files on either NTFS or ext3.  I suggest you google a bit and see the various pros and cons of each.

I think I will go that route but I will obtain more information first. And if you find it and post it I would greatly appreciate it.

---

### Post by aquavitae on 2007-09-07
Sef posted the link to the ext3 driver above: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by rsambuca on 2007-09-07
+1 to the fs-driver for windows.

---

