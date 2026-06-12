---
title: "Best Partition Arrangement"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Archgarth on 2007-04-25
I'm Installing Ubuntu 6.06 on a 180GB IDE hard drive that I plan on using as a windows file storage drive as well.

My ideal situation is to have 150 GB formatted as NTFS, and two other partitions, one for the swap and another for root out of the remaining 30 GB.

For some reason, I can't seem to figure out how to accomplish this properly, maybe I need more partitions than I have currently made.

Reformatting, manually repartitioning the drive is possible, I'm just not sure what the best, and most reasonable way to accomplish this partitioning is.

Any help would be welcome.

---

### Post by LaRoza on 2007-04-25
The easiest way to do this (for me) would be to use GParted LiveCD and format and partition the drive exactly as you have it set up.

If you have Windows installed, be sure to defrag it before partitioning. 

If you have Windows Vista installed, you should edit the partitions with Vista.

---

### Post by MiCovran on 2007-04-25
Here are some good advices for partitioning: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Gina on 2007-04-25
I have a 160GB HD in use as NTFS data for Win XP and several other partitions for Ubuntu.  I Used GParted to resize the NTFS and make new partitions in the space freed.  Just make sure you defrag the NTFS using Windows and check it before resizing.  I find GParted an excellent partition editor and have used it many times now to resize and create partitions.

Yes, the psychocats guide is very good.

---

### Post by az on 2007-04-25
> **Archgarth said:**
> I'm Installing Ubuntu 6.06 on a 180GB IDE hard drive that I plan on using as a windows file storage drive as well.

My ideal situation is to have 150 GB formatted as NTFS, and two other partitions, one for the swap and another for root out of the remaining 30 GB.

For some reason, I can't seem to figure out how to accomplish this properly, maybe I need more partitions than I have currently made.



As you describe it, windows will not be running on this machine, right?  In that case, you do not need to make an ntfs filesystem to share files with windows boxes over the network.  Fileserving over the net is filesystem agnostic, since it is only the local OS that needs to access the disk directly.  Just use ext3.

If you do dual boot, by far the easiest and most powerful way to share files is to use the windows ext2/ext3 driver (fs-driver.org)  It enables Windows to use ext filesystems as native windows ones.

---

### Post by Archgarth on 2007-04-25
> **az said:**
> As you describe it, windows will not be running on this machine, right?  In that case, you do not need to make an ntfs filesystem to share files with windows boxes over the network.  Fileserving over the net is filesystem agnostic, since it is only the local OS that needs to access the disk directly.  Just use ext3.

If you do dual boot, by far the easiest and most powerful way to share files is to use the windows ext2/ext3 driver (fs-driver.org)  It enables Windows to use ext filesystems as native windows ones.

Actually, windows will be running on this machine, so it will be dual-boot, but all of the important windows files will be on a separate drive.

Thanks for the link, I'll check it out.  I was also completely unaware of the ext2/ext3 driver.

---

