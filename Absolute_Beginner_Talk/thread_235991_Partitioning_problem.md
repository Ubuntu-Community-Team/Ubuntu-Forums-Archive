---
title: "Partitioning problem"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by sbu on 2006-08-14
Hi guys and ladies!
I have made two partition with a virtual windows FAT system,using the windows installation disc.On the one partition I installed windows XP and on the other there's nothing.

I am trying to install Dapper 6.06 on the free partition following the GUI procedure but I get a an error saying:'No root file system'.This is even after choosing one partition with '/' and one swap.

Can anybody help,My knowledge about partitioning is very limited I am just doing what somebody told and what Ubuntu website on this sunject told me to do?:sad:

---

### Post by rdd on 2006-08-14
You are definetely going in the right direction. However, Linux does not use the FAT-Filesystem. And while there are many different filesystems for linux, Ubuntu by default uses ext3. 

In order to install Ubuntu, you should delete the second empty FAT partition and leave the space free. In the Ubuntu installer you can select to use the free space on the disk. The installer will then partition that free space for you. 

Regards

rdd

---

### Post by rdd on 2006-08-14
sorry double post

---

