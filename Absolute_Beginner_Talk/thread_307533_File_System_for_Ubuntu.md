---
title: "File System for Ubuntu"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by TreeFinger on 2006-11-26
I am planning on dual booting Ubuntu and Windows XP. I currently am running windows.

I am going to format my main harddrive. What File System do I use for Ubuntu? I also have a secondary harddrive for storage. It is NTFS. Will I be able to look at those files while using Ubuntu? Thank you :D

---

### Post by Smirre on 2006-11-26
You'd normally use the ext3 filesystem.   

And yes, you can read data from your NTFS disks.

---

### Post by turbojugend_gr on 2006-11-26
I aggre with the above post (ext3/yes you will), just wanted to clarify that ubuntu's LiveCD (also known as Desktop CD) can be used to install Ubuntu while actaully running it (Live version of it anyway). SO you can browse the web or this forums for any questions while installing...;)

No back to the topic. You can use the Ubuntu installer to create the partitions.I would suggest you to do os, as using other tools (like partition magic) is sometimes problematic. If you still wish to have your partitions precreated you could use the Gparted liveCD, which is the same tool ubuntu uses to create the partition anyway.

... welcome to UBUNTU!

Cheers, TJ.

---

### Post by shin on 2006-11-26
Right now you can have read/write access to NTFS partitions from linux thanks to ntfs-3g project. There is a howto on this forum how to do it, but usually all you need to do is apt-get install ntfs-3g and change in fstab ntfs to ntfs-3g. Works great.

About filesystem for linux. I never liked ext3, mostly because of it consistency checks every 30 mounts (yeah I know, it can be turned off). On 6.06 I used reiserfs and now I switched to jfs. Why? JFS is the lowest CPU-usage filesystem, it is very fast (faster than ext3 in like every way) and saves your space (with ext3 you waste like 8% of your hdd, with jfs -0.18%).

To be honest - I wanted to try xfs. According to most of benchmarks - it is the best FS now. But I was too lazy to create another /boot partition and installer of ubuntu said that xfs cant be used for /boot. This is strange and I think this is caused just by the lack of staticly compiled module for xfs in ubuntu default kernels.

Conclusions: in most cases it is better to use jfs or xfs over ext3

Reference:
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)
[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

---

### Post by fhqwhgads on 2006-11-26
Hi Treefinger,

Ubuntu will mount NTFS partitions as read-only. As you get more comfortable in Linux this will likely become a pain. FAT32 partitions are read/write under both linux and windows. If you have (or can borrow) an external drive, you could copy your data off, reformat as FAT32 then copy it back. One problem though is that XP will not offer FAT32 as an option for large partitions; linux will. Using the excellent Gparted live CD mentioned above, this should be trivial to do.

As for how the dual-boot filesystem works, here's my setup:
30GB - NTFS - WinXP
13GB - EXT3 - /root (about 9GB free currently)
 2GB - swap (about twice your RAM is good)
Rest - EXT3 - /home
USB2 external is FAT32 for shared data

Careful consideration of your partitioning setup ahead of time will save you a lot of grief in the future. Good luck!

---

### Post by iClouseau88 on 2006-11-26
When I first installed Ubuntu 6.06 LTS, I chose ext3 file system but now whenever I log in I saw the file system shown as ext2 only.  How do I change to ext3?

Thanks in advance.

iClouseau88
Ubuntu Dapper 6.06 LTS

---

