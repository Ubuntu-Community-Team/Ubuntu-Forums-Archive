---
title: "partition help"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2006-10-18
Help, again.
Basically ive got a P3 800mhz pc with a gig of ram and 22ish gb hd and a Gforce 2 graphics card. 
I know ubuntu can run on this, and ive sucessfully run live cd and setup my internet connection.
Now basically i want to dual boot but keep as much of my drive avaliable to windows 98 and ubnutu. How much should i keep for both to use. Im currently using just under 3gb of disk space. Which includes windows. plus is it reversable? without compromising windows?

---

### Post by ReaderRat on 2006-10-18
Well, It's up to you to decide on partitions.
I would go with:
9Gigs - Windoze NTFS
9Gigs - Linux ext3
1Gig - swap
3Gigs fat32 (Which can be read by both OSs)

Info FYI:
[**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)
[**Mount Windoze Partition**](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Kateikyoushi on 2006-10-18
Seems to me he runs win98 on that pc so by using fat32 partition for windows a 4th partition wouldn't be necessary.

---

