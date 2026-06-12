---
title: "Manual Partitioning"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by tototime on 2007-12-01
Hello All,

I need some help with manual partitioning and installing Ubuntu.  I would like to keep xp for a dual boot situation between the two and i was wondering what to partition or add in this table.  If i could get step by step instructions that would be great, thanks.

dev/sda
/dev/sda1   fat16   /media/sda1
/dev/sda2   ntfs    /media/sda2
free space
/dev/sda5  fat32  /media/sda5
/dev/sda4  fat32  /media/sda4

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> Hello All,

I need some help with manual partitioning and installing Ubuntu.  I would like to keep xp for a dual boot situation between the two and i was wondering what to partition or add in this table.  If i could get step by step instructions that would be great, thanks.

dev/sda
/dev/sda1   fat16   /media/sda1
/dev/sda2   ntfs    /media/sda2
free space
/dev/sda5  fat32  /media/sda5
/dev/sda4  fat32  /media/sda4

Hi and the first problem I see is that you already have four partitions on that drive and that is all that you are allowed unless one of the partitions is a extended partition. SO as I see it one of the partitions will have to be deleted and then create a extended partition so you will be able to create the partitions for ubuntu.   
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by tototime on 2007-12-01
how would i go about deleting these which one would i delete if i wanted to keep windows

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> how would i go about deleting these which one would i delete if i wanted to keep windows

Well that is a good question, I would assume that the ntfs partition is the windows but it could also  be a fat 32. You can mount each of the partitions from the live cd and then decide which has your windows partition and which has storage. :KS

---

### Post by st33med on 2007-12-01
> **overdrank said:**
> Well that is a good question, I would assume that the ntfs partition is the windows but it could also  be a fat 32. You can mount each of the partitions from the live cd and then decide which has your windows partition and which has storage. :KS

If you have Windows XP, then it will most likely be (in fact, it should be) the ntfs partition. Those Fat32 partition could be backups, check My Computer and tell us what devices you have (ex :/C, :/F). That Fat16 could be a recovery partition I wouldn't want to delete it.

Go to [http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/") for the LiveCD Gparted.

---

### Post by tototime on 2007-12-01
i have a c:/ drive and a d:/ drive and that is all and the one with the most memory in it is the ntfs partition so i assume this is  windows

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> i have a c:/ drive and a d:/ drive and that is all and the one with the most memory in it is the ntfs partition so i assume this is  windows

Hi and when you assume you can make mistakes. **_Please BACK UP all you data_** before you proceed.

---

### Post by tototime on 2007-12-01
ok i backed up my data so whats next

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> ok i backed up my data so whats next

Ok windows says you only have  c and d drives but your partitions say different
/dev/sda1 fat16 /media/sda1
/dev/sda2 ntfs /media/sda2
free space
/dev/sda5 fat32 /media/sda5
/dev/sda4 fat32 /media/sda4
 SO if you want to keep windows as a dual boot with ubuntu I would take the manual partition option during the install and delete the sda4 and 5 and that is where I would partition and install ubuntu. Those partitions could be your restore partitions for windows so how you proceed is up to you. 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

