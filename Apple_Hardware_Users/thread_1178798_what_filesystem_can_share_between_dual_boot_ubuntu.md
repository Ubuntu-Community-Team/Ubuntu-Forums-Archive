---
title: "what filesystem can share between dual boot ubuntu osx"
date: 2009-06-04
forum: Apple Hardware Users
---

### Post by nephish on 2009-06-04
hey all,
i have a macbook and ubuntu dual booting. I have a drive partition of 180GB that only the ubuntu box can mount. 
Is there a way to use that drive partition by both Operating systems?

If so, how, and what filesystem do i use?

thanks

---

### Post by tiagobt on 2009-06-04
> **nephish said:**
> 
If so, how, and what filesystem do i use?


HFS+ works well in Mac OS X, but is read-only in Linux.

Ext3 works well in Linux, but is not supported by Mac OS X (although you could try [ext2fsd](http://ext2fsd.sourceforge.net)).

FAT32 works well on both systems, but is an old file system. However, if you don't need advanced features (such as file encryption), FAT32 is still a good option.

NTFS works well on both systems as long as you have [NTFS-3G](http://www.ntfs-3g.org) installed. Although NTFS is a Windows file system (which you're not using), I think this is the best choice (NTFS-3G is pretty stable now). Ubuntu already comes with NTFS-3G, so you just have to install [NTFS-3G for Mac OS X](http://macntfs-3g.blogspot.com), which is just one package now.

---

### Post by tiresia on 2009-06-05
> **tiagobt said:**
> HFS+ works well in Mac OS X, but is read-only in Linux.
Only partially true ;) If HFS+ is *not* journaled, also Linux can write to an HFS+ Partition.
Gparted can resize/shrink HFS+ Partition, but it can't generate an HFS+ File System.

Therefore I prefer to have a HFS+ not Journaled Share Partition for both Systems

---

### Post by maflynn on 2009-06-05
> **tiresia said:**
> Gparted can resize/shrink HFS+ Partition, but it can't generate an HFS+ File System.

Therefore I prefer to have a HFS+ not Journaled Share Partition for both Systems
I've only been able to shrink my HFS+ partition with Gparted and not grow it.  Something to consider.

---

### Post by cyberdork33 on 2009-06-05
> **tiresia said:**
>  Gparted can resize/shrink HFS+ Partition, but it can't generate an HFS+ File System.

> **maflynn said:**
> I've only been able to shrink my HFS+ partition with Gparted and not grow it.  Something to consider.

yes, that is correct. parted can only shrink not grow hfs+. I also thought that you could now create a new hfs+ partition, but they may have taken that feature out again if it was buggy. PartedMagic used to support it I believe.

---

### Post by nephish on 2009-06-05
ok, thanks for the help, Gents. I will give it a shot this weekend and post here how it went.

---

