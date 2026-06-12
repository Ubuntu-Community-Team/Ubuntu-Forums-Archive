---
title: "Help bad! Ubuntu's partition size is too large"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Newbie2929292 on 2006-10-13
Help me please.:D 
I installed Ubuntu but chose the wrong partition sizes.:( 
I have 111 gb harddrive i meant to keep Windows XP media center larger than Ubuntu but i messed up.:( 
Now Ubuntu has most of my space it took all but 40.4gb it gave to WinXP and the rest is ubuntu!
How do i fix this do i have to unistall it and will i get the room back.:KS

---

### Post by Newbie2929292 on 2006-10-13
and if ya can plz answer the question that how do you get the internet going:rolleyes:

---

### Post by elchinovi on 2006-10-13
I know that if you use GPartEd, you can shrink NTFS partitions to make room for Ubuntu, but I'm not sure if it can expand shrunken partitions...
See if that works...
I'm sure that someone more experienced will be able to answer this better
Good luck!

---

### Post by aysiu on 2006-10-13
What I've always been told is that you can resize the end of a partition but not the beginning of it.

So if you delete the Ubuntu partition, you can probably resize (i.e., expand the NTFS one), but you can't just shrink Ubuntu's to make more room for NTFS.

Did you choose the "Automatically Resize" option?

---

### Post by mahy on 2006-10-13
> **elchinovi said:**
> I know that if you use GPartEd, you can shrink NTFS partitions to make room for Ubuntu, but I'm not sure if it can expand shrunken partitions...
See if that works...
I'm sure that someone more experienced will be able to answer this better
Good luck!

If not in GParted, maybe in some windows utils such as Acronis DiskDirector Suite and Symantec Partition Magic (both paid software!!), that doesn't matter. NTFS can be expanded. The question is, what's your linux filesystem? I've heard that reiserfs can't be shrunk... If that's the case, you'll have to reinstall your Ubuntu.

---

### Post by Herman on 2006-10-13
Actually GParted has been able to resize all kinds of partitions from either end, or 'move' all kinds of partitions for some time now.

However, the version of GParted that comes with Ubuntu might not be the latest up to date one. New versions of Ubuntu are released about every six months, (which is fast for an operating system), but a new edition of GParted LiveCD has been released about every two or three weeks. It is almost time for Edgy, so some of the Dapper applications are almost six months old, which is ancient as far as GParted is concerned.

If you want to use the latest GParted on its own live cd, it is free, and less than 30 mb to download, here, [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")

Gparted, being 'Parted based, is fully compatable with Ubuntu and Grub, so it is unlikely harm your installations. It is also safe to use with with NTFS. (You can even create NTFS filesystems with it.)
As with any partitioning work though, always back up data first to be sure.

Regards, Herman :D

---

