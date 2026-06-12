---
title: "Is there..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Stu Ruckus on 2008-01-26
...where do I find my partitions and how would I get rid of my xp dual boot without having to reinstall linux?

---

### Post by taurus on 2008-01-26
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
You can use gparted (System -> Administration) to convert your windows partition to a storage space, ext3 filesystem.  But if you want to merge that free space into Linux, then you need to do that from either the LiveCD or GParted LiveCD.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Odd-rationale on 2008-01-26
I would use GParted. It is in the Ubuntu LiveCD or you can download a GParted LiveCD here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Step #1: BACKUP YOUR DATA.

Resizing partitions can be somewhat risky. Don't take the chance!

Boot up the LiveCD and start GParted. Delete your windows partition and expand the ubuntu partition to fill up the freed space.

When it is down, reboot into Ubuntu. If the Windows boot entry is still there, do
```
sudo update-grub
```
in ubuntu.

Hope that helps.

---

### Post by Odd-rationale on 2008-01-26
Sorry, I didn't mean to be redundant...

---

### Post by antisocialist on 2008-01-26
boot up teh good ol' liveCD and open a terminal
type
sudo gparted
and it will run gparted, a partition manager

from there you will choose delete for the windows partition, and then on your linux partition choose expand, and set it so that there is 0 space left when you are done

---

