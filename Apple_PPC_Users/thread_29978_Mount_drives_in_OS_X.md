---
title: "Mount drives in OS X?"
date: 2005-04-26
forum: Apple PPC Users
---

### Post by NorthernSoul on 2005-04-26
First off, thanks to everyone who works on Ubuntu. I just started using it and I love it. Now to my question. Like many users, I partitioned my hard drive in order to run two different operating systems, in this case being Ubuntu (of course) and OS X. As well as partitioning the hard drive in to two seperate pieces to accomplish this, I also made a fat32 partition with the intention of it being accesible from both operating systems. Unfortunately, it doesn't seem to show up in OS X. Is there any way I could make OS X mount it? Thanks for the help.

---

### Post by DJ_Max on 2005-04-26
Have you looked at
[http://ubuntuppc.info/Misc/MountOSXOnTheFly](http://ubuntuppc.info/Misc/MountOSXOnTheFly)

---

### Post by Len on 2005-04-26
You could also install Ext2FS if you have formatted your Ubuntu drive(s) in ext2 or ext3 format:
[http://www.macupdate.com/info.php/id/11657](http://www.macupdate.com/info.php/id/11657)

This way OS X can read your linux partitions like any other. They'll just show up on the desktop (or not, if you configure it to mount only specific partitions).

Just put another filesystem on that partition that is now fat32 and you're set.

This command mounts HFS+ filesystems within linux (the link of DJ_Max also explains):
```
mount -t hfsplus /dev/hd**xx** /mount/somewhere
```

---

### Post by NorthernSoul on 2005-04-27
Thanks for your help guys. I like the program you suggested Len. Now that I'm going to reformat the partition, do I have to do it through the installation program? Is there a way I could do it without having to go through the installation process?

---

