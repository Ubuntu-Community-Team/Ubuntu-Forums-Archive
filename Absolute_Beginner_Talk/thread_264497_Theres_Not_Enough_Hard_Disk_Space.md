---
title: "Theres Not Enough Hard Disk Space"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-09-24
Hello!
I defragmented my d: drive about an hour and waited for you to reply.You said to 'resize" my drive.How to do that?

---

### Post by MWAAAHAAA on 2006-09-24
From this and your previous post, I think you need some background info. Check out the following [http://www.tldp.org/HOWTO/Partition/index.html](http://www.tldp.org/HOWTO/Partition/index.html).

---

### Post by crokett on 2006-09-24
> **Sterbik said:**
> Hello!
I defragmented my d: drive about an hour and waited for you to reply.You said to 'resize" my drive.How to do that?

The link MWAAHAA posted is a good one.  And you do need to do some background reading on partitions.  

From your posts it appears you have a 20GB drive split into 2 partitions.  So you either need to reformat one for Ubuntu to use - in which case you lose all the data currently on that partition, or you need to resize the partition to create free space on the disk. 

When you boot the Ubuntu install CD you can start a terminal session and run a partitioning tool called gparted.  However **UNLESS YOU KNOW WHAT YOU ARE DOING YOU WILL LOSE DATA**.  So either do enough reading to make sure you know what you are doing, have a friend help or buy another HDD and install Ubuntu on that.

---

