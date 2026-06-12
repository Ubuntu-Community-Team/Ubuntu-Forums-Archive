---
title: "Creating a FAT32 Partition"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by think13 on 2006-09-24
I just installed ubuntu, a dual-boot with windows, and I want to create a FAT32 partition so I can share files between the two OS's by shrinking the Windows partition and creating a new FAT32 'shared' partition.

I downloaded the package QTParted, but for some reason it won't let me shrink the windows partition.  It doesn't give me any options to do with that partition.  Do I need to do this in Windows?  I don't know if I trust third-party windows software editing my partitions.

I have attached a screenshot of what I get.

---

### Post by kidders on 2006-09-24
What's on /dev/sda1?

---

### Post by think13 on 2006-09-24
dev/sda1 is the NTFS Windows partition.

---

### Post by kidders on 2006-09-25
Hmm... Your screenshot ("Cannot unmount partition...") suggest that, for some reason, the system can't dismount it. This might happen if it's in use. To check whether it is...

1. **Find out where it is**
Use the output of "mount" to identify the filesystem mount point for /dev/sda1.

2. **Find out what's open**
Say the mount point is /mnt/windoze. Running "lsof | grep /mnt/windoze" should return no output, if no files are in use on the disk.

Partition editors sometimes need to dismount devices, because tinkering with partitions while they're still being used can be ... well ... dangerous.

---

### Post by NewbieLearnLinux on 2006-09-25
Well, you can read/write NTFS volumes with ntfs-3g driver. See this How-To:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

And explore2fs allows you access Linux partitions (ext2/ext3) in Windoze:
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by forked on 2006-09-25
I am having a similar problem.
I wanted to share one Thunderbird Profile and Mail Archive amongst  XP32, XP64, and Ubuntu 6.06.

Over in the Tbird forums, they suggested that I make a FAT32 partition for the profile and point all installations of Tbird there.
[http://forums.mozillazine.org/viewtopic.php?p=2507365&sid=cd63b0a0b60f874ad7fe9f6ee0bca2a1#2507365](http://forums.mozillazine.org/viewtopic.php?p=2507365&sid=cd63b0a0b60f874ad7fe9f6ee0bca2a1#2507365)

I did that, but Ubuntu sees the Tbird partition, but can't mount it.

Would I be better off trying that thing that will let Ubuntu read NTFS?

---

### Post by think13 on 2006-09-25
Instead of using a FAT32 new partition,  I simply used the one mentioned in the link above that lets windows see ext3 partitions.  It worked like a charm!

Now I want to shrink my Windows NTFS partition and grow my Linux one.  QTParted is not helping.  It won't let me do anything to the NTFS partition.

---

### Post by forked on 2006-09-26
I shrunk my NTFS partion with Acronis Disk Director.

---

