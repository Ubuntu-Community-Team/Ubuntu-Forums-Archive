---
title: "A Ubuntu/XP Dual Boot Question Involving writing to XP partitio"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by strtpls3 on 2007-05-23
Hello all,

      I'm extremely new to Linux but I am already happy I installed Ubuntu. I found a bunch of posts on issues partitioning hard drives themselves I didn't find the answer to my problem (I may just be looking in the wrong place).  I have Ubuntu/XP dual boot through Grub on a 120 GB drive.  I gave XP 64gb the swap partition 1GB and Ubuntu 55gb.  I cannot see the Ubuntu partition from XP (not shocking).  However, it does looks like I can see the XP partition in Ubuntu and its labeled "hda3".  I cannot however, edit/write to this partition. I understand that may be due to Linux not being able to read NTFS formated partitions. On an interesting note, the Ubuntu partition seems to be taking up 60GB as well (or am I wrong that" \" or "file system" is the Ubuntu partition)?         

      What method should I use to reencode the new XP and Ubuntu partitions in order to be able to access both partitions from either OS (if this is even possible) or both just from Ubuntu.  I don't mind for example, reinstalling both Ubuntu and XP into a ext3 format if anyone can tell me that this won't have any detrimental effects on XP.  Also, would It be possible to rename visible drives/partitions?  for Example, I would like the windows partion to read "windows" instead of "hda3" and my os drive in Windows to be named "C" again and not the "G" that it has changed itself to.

     Sorry I'm asking so many questions in 1 shot but I would like to get both OS running as interconnected and reliably as possible to balance work (XP) and home (Ubuntu) on one laptop.

Thank you all for your help!

Strtpls3

---

### Post by Seisen on 2007-05-23
To be able to read/write to your Windows partion in Ubuntu you need ntfs3 here is a link on how to install it.

[http://lunapark6.com/?p=1710]("http://lunapark6.com/?p=1710")

---

### Post by lopagof on 2007-05-23
you need some ntfs drivers.]

dont worry its a common problem.

---

### Post by annda on 2007-05-23
if you want to access the linu partition(s) from windows, you will need this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by strtpls3 on 2007-05-23
THANKS ANNDA AND SEISEN! Both programs work like a charm!  Just one question though.  Does  it matter that my linux partition is in ext3 and not ext2 as fs-driver recommends?  Is there any real difference between ext2 and ext3 as far as reading and writing is concerned?  Seems to be working fine so far though...

Thanks again guys,

Strtpls3

---

### Post by Hobo Joe on 2007-05-23
> **strtpls3 said:**
> Does  it matter that my linux partition is in ext3 and not ext2 as fs-driver recommends?  Is there any real difference between ext2 and ext3 as far as reading and writing is concerned?  Seems to be working fine so far though...

Strtpls3

Don't worry, you'll be fine as far as that goes.

---

