---
title: "n00b questions. concerning HD space, partitions, etc"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ccclairee on 2007-08-15
**Question 1.**

I have a 80 GB hardrive. I've moved my extensive music and video collection to external sources (my Zune), also most of my pictures. I uninstalled all programs I can spare, I've deleted temp files and defragged several times. After all this, I have 13.67 GB free space on my C drive, this is 40% free space.
On my E drive, 37.18, or 99% free space. What is the E drive? Is it relevant to what I'm doing? Do I worry about it? Or do I just worry about the C drive? There's not enough space on the C drive though, is there? Oh my.

**Question 2.**

There is a partitioning program on the Ubuntu disk, right? So I don't have to pre-partition my hardrive before I boot from the Ubuntu cd? I want to create a shared FAT32 partition, so this means I have a primary (windows) partition, a / partition, a swap partition and the FAT32 partition? So 4 partitions total. How to I put the data I want to share between OS's in the FAT32 partition?

---

### Post by Hospadar on 2007-08-15
Hellos!

1) It sounds like you already have two partitions on your 80 gb harddrive, the "c" (where windows is installed presumably) partition and the "e" partition.  My suggestion would be to reformat the "e" partition ext3 (the filesystem used by ubuntu) and install ubuntu there.

What you will want to do is delete that partition (make sure you don't have data you want to save there!) create a small swap, and ext3 (with enough space and some more for linux) and then another ntfs partition in the free space that came from deleting the e partition.

I would say use ntfs instead of fat32 for cross-OS sharing because it's way better than fat32 and with ntfs-3g, you can get full read-write support for ntfs with linux.

2)
Yes, there is a partitioner on the install disk.  If you open up a terminal (Applications->Accessories->Terminal) type "gparted".  There is also a partitioner in the install process itself, but gparted is a little more full featured.

You can also get a different livecd that just has gparted on it if you have trouble with the partitioners on the ubuntu livecd:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

As for sharing between ms and linux, Linux can mount your ntfs partitions and with ntfs-3g you can write data to them and then that stuff will be on those partitions when you boot into windows.  You can also get ext3 drivers for windows, Although having a seperate partition for sharing is always safer, because you might accidentally corrupt the other os if you are writing stuff to the partition where it is installed.

hope this helps some!

---

### Post by dptxp on 2007-08-15
You have C drive and E drive, where is D drive ?

A safe way is to (during installation) delete the E drive, resize to 6-8 GB for / (roo), resize rest minus 1-2 GB for data (give any name and it can be FAT32, Linux read FAT32), last 1-2 GB for SWAP.

Thus you do not touch the Windows partition, and can read it from Linux.

---

### Post by Inxsible on 2007-08-15
My advice would be to partition your drives manually before the install. That way you are sure of how your drives are structured and you can then install Linux in exactly the drive you want, instead of hoping for the best using the automatic partitioning.

Are you sure the E drive is not the external drive ?

---

### Post by ccclairee on 2007-08-15
Thanks for the replies.

> **Hospadar said:**
> Hellos!

 My suggestion would be to reformat the "e" partition ext3 (the filesystem used by ubuntu) and install ubuntu there.




All my E drive has on it is a 280 KB .txt file. 

```
=== Verbose logging started: 11/16/2006  19:01:39  Build type: SHIP UNICODE 3.01.4000.2435  Calling process: C:\WINDOWS\system32\msiexec.exe ===
MSI (c) (60:48) [19:01:39:078]: Resetting cached policy values
MSI (c) (60:48) [19:01:39:078]: Machine policy value 'Debug' is 0
MSI (c) (60:48) [19:01:39:078]: ******* RunEngine:
           ******* Product: e:\d508b9242f83a7610fb5f9f032db\msxml.msi
           ******* Action: 
           ******* CommandLine: **********
```

etcetera... this goes on for 280 KB worth. It kind of looks important. I feel I shouldn't reformat and get rid of this? Could I maybe just shrink it or might this mess something up?


> **Inxsible said:**
> 
Are you sure the E drive is not the external drive ?

I have Local Disk (C: ), DVD/CD-RW Drive (D: ), and Local Disk (E: )

---

### Post by Inxsible on 2007-08-15
> **ccclairee said:**
> I have Local Disk (C: ), DVD/CD-RW Drive (D: ), and Local Disk (E: )

That hardly says anything about it being external or internal.

Normally, internal drives are listed before the Cd-DVD drives. That's why I thought it might be an external drive. 

Do you have any external USB drives attached to the computer ?

---

### Post by ccclairee on 2007-08-15
No, I don't have any external USB drives.

---

### Post by ccclairee on 2007-08-16
this post has fallen back pages, bumping it up. don't know if this is frowned upon but I really want to figure this out :-/

---

### Post by Chaotic Thought on 2007-08-16
Unfortunately, you can't tell by looking at the drive letters what the C:, D:, E:, etc... actually are. Try this:

Control Panel -> Administrative Tools -> Computer Management

And then choose "Disks" in the left pane. It shows you exactly what drives you have and which drive letters they are mounted on. For example "E:" is probably an extended partition on your primary hard disk.

If it's large enough, just remove your "E:" and use it for Linux. You can do this from within Windows as well--that way you can just point Linux to that partition when you're going to install. 


P.s> The MSI logfile that's currently on your E: partition is trash--it has a random directory name in it and looks like it was created as a temporary working area by some installer.

---

### Post by ccclairee on 2007-08-16
Thank you!

Problem solved I think.

---

