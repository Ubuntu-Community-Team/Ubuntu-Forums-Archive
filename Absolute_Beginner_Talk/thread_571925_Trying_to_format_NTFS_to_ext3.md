---
title: "Trying to format NTFS to ext3"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tdk2fe on 2007-10-09
Hello,

I recently got the Xubuntu Feisty Fawn cd and i'm trying to use it to format one of my old PC's.  Right now it has a 120gig hd formatted in NTFS (was running windows XP).  When I go into Gpart, it says that it cannot create a disklabel.  When I try to use fdisk, it says that it cannot open the path.  Gpart says the device is at /dev/hde.  I've tried the following with fdisk:

fdisk /dev/hde
fdisk /dev/hde1

fdisk -l /dev/hde (no output)

I was wondering if anybody had this problem before as I can't find any previous threads like it.  Is there some other format/partitioning tool I could be using?  I know the disk isn't bad, as it right now has a fully working fresh copy of Win XP on there that works fine.  Any and all help would be much appreciated - thanks in advance.  

Regards

---

### Post by Drakkor on 2007-10-09
Why not just put the Fiesty CD in, and use the whole disk ??

---

### Post by Pumalite on 2007-10-09
Use Gparted (the stand alone program):[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

