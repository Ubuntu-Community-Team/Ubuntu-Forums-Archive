---
title: "Can I change this:external ntfs hd?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-04-18
Hi-
I feel kind of dumb asking this but, it seems, I can't get this ntfs/fat32 thing through my thick head! 
Here is the short story.
I've got an usb external 80G hd in ntfs and would 'simply' like to use it with Ubuntu.From what I understand, I can't because it is in ntfs.
I'd like to use it as a go-between win... and Ubuntu or try to install Dapper on it to try.
Is there a way? thanks in adv

---

### Post by OffHand on 2006-04-18
You will have to format it fat32. Both Linux and Windows can read/write to fat32. You can only read ntfs from Ubuntu. Note that if you format it, all data will be lost.

---

### Post by malavar on 2006-04-18
you can resize the ntfs partition, and use the free space left over to create ext3 or ext2 file systems to house your linux system, its not very complicated so dont worry. :)

---

### Post by steve.horsley on 2006-04-18
NTFS is a proprietary secret file system. MS won't publish the specs. You may have some luck with a thing called captive NTFS, which uses the DLL copied from Windows under Linux, but of course you will have to pay for another copy of Windows to legally do that.

FAT is limited in both file size and overall partition size. I suggest you use ext2. Ext2 uses a publicly available format, and there are drivers available for Windows.

---

### Post by xyz on 2006-04-18
Thanks a lot guys!
For some reason, I thought that once a hd is in ntfs.."WINDOWS HAD WON!"...I mean, one could NEVER change that "ntfs fact".
I'm so glad to hear that it's just a matter of (re) formatting the hd! I've got nothing important in it.
I'm just so glad win...didn't win.This windows thing is freaky...the way they do it.

---

### Post by OffHand on 2006-04-18
Limitations fat32:

Prior to NTFS, Windows computers used a file system called FAT32. This system uses 32-bit cluster numbers, which in theory should allow for hard drives up to 2 Terabytes (about 2,000 Gigabytes) in size. FAT32, however, limits file sizes to a maximum of 4 GB and Microsoft limited FAT32 partitions to a maximum of 32 GB.

From: [http://www.build-your-own-computer.info/Hard-Drives-Explained-Part1.html](http://www.build-your-own-computer.info/Hard-Drives-Explained-Part1.html)

---

### Post by syg00 on 2006-04-18
There are efforts out there to enable write support for NTFS.
Captive is one that will work on BB if you have XP on the same system.

ntfsmount using fuse in userspace also has good reports - not really much help below 2.6.15 though.
Haven't tried Dapper, so can't comment.

My recommendation is also to stick to fat32.

---

### Post by xyz on 2006-04-18
Excellent explanation...and the link says it all!
many thanks for your time.

Yes...I've heard about fuse but I think I'll stick to fat32.

---

