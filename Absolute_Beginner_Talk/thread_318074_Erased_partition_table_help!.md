---
title: "Erased partition table: help!"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-13
Hi,

I did a very very stupid thing: 
I had a dualboot system with XP and I wanted to reinstall Ubuntu so I formated the Ubuntu partition. GRUB was installed in the MBR but since it also has some file on the Ubuntu partition, I couldn't even boot XP anymore. Then I thought that it would be simple to reset the MBR using fdisk /mbr......that's right, this was really easy but I also erased the partition table of the harddrive :evil: I have backups for most of my files but I'd like to recover some that were on a shared (Ubuntu-XP) partition. This partition contained my /home folder. This partition is formatted Ext3.

So basically now that I erased the partition table information, I have no access to my partitions since all programs believe my disk is unpartitionned (GParted on the live CD show that my disk is just unallocated space!). I'd like to know if there is a way to retrieve some of my data (I have backups for most things but I miss a few files) on the shared partition? Is it possible to rebuild a partition table????


Thanks

---

### Post by louieb on 2006-12-13
I have never used it, but I've seen it referred to in other threads, you might try [B][URL="http://www.cgsecurity.org/wiki/TestDisk"]TestDisk 
[/URL][/B] Let me know how it worked out.

---

### Post by kilou on 2006-12-14
Thanks for your help. I tried Testdisk but I couldn't see anything left on the disk. I also tried to rebuild the partitions (same sizes) with GParted without formatting them. I read somewhere that this would rebuild the partition table and may possibly allow to re-access the data on the partitions........but it didn't work for me :( I think I'm stuck and I'll have to reinstall everything. Not too bad since I have backups but I'll lose my bookmarks and some other things that were important to rebuild the system.

Anyway...

---

### Post by Sef on 2006-12-14
Try [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by housam on 2006-12-14
Read [this]("http://community.linux.com/howtos/Partition/index.shtml") as it has a section for recovery

---

### Post by kilou on 2006-12-15
Thanks for all your help guys! That's really appreciated. But I think I've messed with things too far and cannot get anything retrieved with all the methods above. So I decided to reformat the disk, rebuild the partitions and restart with a clean install (I have a Ghost image for XP but nothing for Ubuntu). However this will allow me to reinstall Ubuntu using the alternate CD and get a bit more control on what I'm doing, which is not a bad thing for a newbie anyway :-D 

Thanks again for your help!

---

### Post by John E on 2006-12-15
If you know anyone with Partition Magic, get them to make you a rescue disk. It has an option to find erased partitions and I've never known it to fail.

But do it soon - before you do anything else with that drive!!

---

### Post by ZERO_SHIFT on 2006-12-15
Gparted Live CD is Great too.

---

