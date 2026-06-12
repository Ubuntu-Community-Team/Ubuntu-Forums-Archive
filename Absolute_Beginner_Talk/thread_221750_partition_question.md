---
title: "partition question"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by fedekiller on 2006-07-23
Hi all! i want to install linux in a partition, but before making one with partition magic, do i have to make it linux ntfs or fat32 or... :-k

---

### Post by Freddie.Ruddick on 2006-07-23
It doesn't really matter. If you can, you may as well leave it unformatted. The ubuntu installer will take care of formatting for you. Just make sure that you don't accidentally select "Delete all partitions and install Ubuntu" in the installer.

HTH

---

### Post by fedekiller on 2006-07-23
hehe k thanks ^^ anyways i will defragment and stuff first :mrgreen: thanks

---

### Post by Sef on 2006-07-23
> but before making one with partition magic,

Don't use partition magic.  It and linux do not get along well.  Better to use [GParted]("http://gparted.sourceforge.net/livecd.php"), [QtParted]("http://qtparted.sourceforge.net/"), or [DiskDrake]("http://pclinuxos.com/news.php") from PCLinuxos. It is part of the os.  If you want a commercial one Acronis is good.

> do i have to make it linux ntfs or fat32 or

Make it either ext3 or reiferfs.  FAT 32, ext2, and ext3 can be both read and written to by Linux and Microsoft.  NTFS is Microsoft's proprietary file system, which Linux can only read.

---

### Post by fedekiller on 2006-07-23
thanks :D but those programs are for linux x_x im using windows now

---

### Post by Sef on 2006-07-24
> thanks  but those programs are for linux x_x im using windows now

You can still download them and burn them to a cd.  They work off of a cd.

---

### Post by fedekiller on 2006-07-24
aw great :) thanks :mrgreen:

---

### Post by Sef on 2006-07-24
You are welcome.  Please post any more questions you have.  If it is on a different subject, then start a new thread.

---

