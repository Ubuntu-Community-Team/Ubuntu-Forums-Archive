---
title: "Partition type?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-08-22
Hi, 
I have recently resized my Windows XP NTFS partition, and I was left with 20.93 unallocated GBs.  I want to expand my ubuntu partition, but when I click resize gParted only lets me make it smaller, if I make a new one, will ubuntu be able to write on it (ext3) or will it be read-only? also, when I try to make a new one the only option I have is to make it a Primary partition, is this correct if I want to make a new writable partition?

thanks

[http://ihostupost.com/files/397/jojojo.png](http://ihostupost.com/files/397/jojojo.png)

---

### Post by annda on 2007-08-22
yes to all questions except read-only: you will be able to writo this new partition under ubuntu and windows (this needs drivers).

also, i haven't tried it but read that it's possible to move a partition and then enlarge it (like move to the left, enlarge to the right).

however, i highly recommend a data partition that does not host any OS's - perfect for backups when reinstalling, doing risky upgrades and so on. ext3 is good for that purpose.

---

### Post by kidcharles on 2007-08-22
I believe there is a limit of 3 primary and 1 extended partitions on a drive, and the extended partition can be subdivided into many partitions. You currently have 2 primary and 1 extended partitions, so you must make that space a primary partition. This should be fine though. If you use the ext3 filesystem it will be fully readable/writeable with Ubuntu. The only real issue Ubuntu has with writing to filesystems is with NTFS drives, because Microsoft hasn't released the full specifications for this type of filesystem. Every other major filesystem is fully supported in linux.

---

### Post by A$h X on 2007-08-22
Use Gparted live CD to format the unpartitioned space as FAT32. That way both Ubuntu and windows can read/write to it.

---

### Post by kidcharles on 2007-08-22
It's true that FAT32 would be usable by both the Windows and Ubuntu OS's, but ext3 is a much more modern filesystem with numerous advantages. I'd only use FAT32 if you absolutely need the drive to be visible in Windows.

---

### Post by logos34 on 2007-08-22
> **A$h X said:**
> Use Gparted live CD to format the unpartitioned space as FAT32. That way both Ubuntu and windows can read/write to it.

I'd encourage you to make a ext3 data partition or better yet [convert it to your /home]("http://www.psychocats.net/ubuntu/separatehome").

Get **fs-driver** to add r+w ext2/3 support to windows.

---

### Post by bodhi.zazen on 2007-08-22
> **federicotedin said:**
> Hi, 
I have recently resized my Windows XP NTFS partition, and I was left with 20.93 unallocated GBs.  I want to expand my ubuntu partition, but when I click resize gParted only lets me make it smaller, if I make a new one, will ubuntu be able to write on it (ext3) or will it be read-only? also, when I try to make a new one the only option I have is to make it a Primary partition, is this correct if I want to make a new writable partition?

thanks

[http://ihostupost.com/files/397/jojojo.png](http://ihostupost.com/files/397/jojojo.png)

Lots of good advice on this thread already.

A few finer points :

First, you can not re-size a mounted partition, thus the advice to resize with a live CD.

Second, you need a newer version of gparted, thus the advice to use the gparted live CD.

Third, if you resize your partiton you may need to edit /etc/fstab as the UUID of the partition may change.

Fourth, if you move the partition =you may need to reinstall or reconfigure grub.

I am not sure if you know how to do these things (#3 and #4) , so I will give you some links :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by federicotedin on 2007-08-22
thanks for the advice, i created a new ext3 partition but it is read-only, how can i make it writeable (i made it as a primary partition, the only choice)

---

### Post by bodhi.zazen on 2007-08-22
sudo chmod 777

Take a look at chown and chmod

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

