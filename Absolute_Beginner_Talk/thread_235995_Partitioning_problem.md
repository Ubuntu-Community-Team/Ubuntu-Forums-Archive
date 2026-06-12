---
title: "Partitioning problem"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by sbu on 2006-08-14
Hi guys and ladies!
I have made two partition(on a 40 GB hard drive) which have a virtual windows FAT file system.I created them by using the windows installation disc.On the one partition I installed windows XP and on the other there's nothing.

I am trying to install Dapper 6.06 on the free partition following the GUI procedure but I get an error saying:'No root file system'.This is even after choosing one partition with '/' and one swap.

Can anybody help,My knowledge about partitioning is very limited I am just doing what somebody told and what Ubuntu websites on this sunject told me to do?:sad:

---

### Post by Contrid on 2006-08-14
Hey there,

I'm new to Ubuntu, but I've been working on these installations and stuff over the past few days. (playing around, etc).

When you look at the partition table, what do you have? Can you give us a screenshot? You should have 2-3 partitions for Linux. The first will be a primary ext3 partition which you will use as root (/). Then you will have a SWAP partition. And if you want to, you can create a third one which will also be a primary ext3 partition for you settings and files (/home).

I think that you cannot create more than 4 primary partitions on your disk, so you will need to create a logical partition, and then divide to create more partitions. But you possibly don't need/have more than 4 overall.

Contrid.

---

### Post by cjm5229 on 2006-08-14
I've had that problem trying to install from the live CD also. I found that after partioning the HDD, most of the time I have to restart and boot back into the live CD to get it to accept the partitions. It seems like there is still a lot of problems with installing from the live CD. It also takes at least 512mb of Ram or it will hang up. I just use the alternate CD anymore, It;s not as pretty but at least it works.

---

