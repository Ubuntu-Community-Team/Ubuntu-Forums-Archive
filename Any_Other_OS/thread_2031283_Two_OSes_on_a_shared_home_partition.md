---
title: "Two OSes on a shared /home partition"
date: 2012-07-21
forum: Any Other OS
---

### Post by L R C on 2012-07-21
Hey guys,

Right now I've got this setup:

sda1 - Ubuntu 11.10, root partition, ~100GB
sda2 - Windows 7 (sorry!) ~170GB
sda3 - Ubuntu 11.10, /home partition, ~480GB
sda4 - Extended partition containing sda5, a swap partition (4GB)

I was planning on installing SolusOS (it's Debian-based if that helps) by shrinking my home partition to make a partition of around 50GB. I want to have SolusOS use the same home partition as Ubuntu so I could share my documents without having to mount partitions all the time, etc. My question is this: if I tell SolusOS to use sda3 as its home partition, will it erase all my data that I already have on it from my Ubuntu install?

Also, will I run into problems with having more than 4 partitions? I don't know if this is an issue with the Windows bootloader (I'm using GRUB), or with the BIOS...

Thanks a lot, and sorry if this is in the wrong subforum.

---

### Post by oldfred on 2012-07-21
You cannot have more than 4 primary partitions. But you can shrink /home and expand the extended partition left into the unallocated and then create new logical partition(s) in the extended.

Those who say you can share /home partition assume you use a different user id so different versions even of Ubuntu do not have user setting conflicts. That really defeats the idea of sharing.

If Debian based and userID is 1000, then a shared data partition or a NTFS shared data partition so you can also shared data with Windows. I have both. I used my NTFS shared a lot when I still booted XP and still have my Firefox & Thunderbird profiles in the NTFS partition. Then it does not matter which Ubuntu or XP I booted, all my email & bookmarks were identical.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by ajgreeny on 2012-07-21
You can't do that as you already have 4 partitions on the disk, the maximum that you can have with a standard msdos MBR and BIOS.  It is unwise to share a home folder with another OS, in any case, as there may be configuration problems from different versions of the same applications in each OS.  You could use the same partition but a different username and therefore different home folder within that partition.

However your main problem is that you can not make a new partition for root of SolusOS without a considerable amount of backing up, sorting of partitions and /etc/fstab of your ubuntu./  The simplest way would be to backup your current /home partition to an external disk, delete the /home and swap, and in the then unallocated space make a new extended partition in which you can make as many logical partitions as you are ever likely to want.

EDIT:
Silly me!  I did not think about doing it oldfred's way which will be quicker, however, I still think it is worth considering linking folders from ubuntu's home to solus's home to save any duplication, or using a separate /data partition for all OSs, including windows, if it's an ntfs partition that you use.

Start with a new swap partition then a new ubuntu /home partition, but leave around 10 - 15 GB free for SolusOS root partition.  Leave solus's home in root but once installed link your ubuntu /home's data folders to the data folders of Solus, so you will then have no duplicate files, but will avoid the problems of a shared /home.

Once you have done that you will need to edit /etc/fstab in ubuntu to take account of the new /home and swap partition UUIDs, which you can find with ```
sudo blkid -c /dev/null
```

---

### Post by L R C on 2012-07-21
Thanks oldfred and ajgreeny, I might end up not using a /home partition for SolusOS after all and just linking folders instead. Expanding the existing extending partition is a great idea, I think I'll do that. Thanks guys!

---

