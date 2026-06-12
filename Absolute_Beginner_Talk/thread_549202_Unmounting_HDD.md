---
title: "Unmounting HDD"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by redmonster13 on 2007-09-12
I am trying to unmount my secondary HDD so that I can reformat it and install windows on it. I have tried using the gparted live cd to do this but I cant get the graphical client to run and I am not confident enough with the command line to do it that way.

The secondary hdd is located at /media/sdb1 and I have tried

sudo unmount /media/sdb1 

the result was command unknown unmount
(or something to that effect)


any help I can get with formating this drive to ntfs would be greatly appreciated.

---

### Post by bubbalouie on 2007-09-12
Try **umount** instead.

I have always used QTParted **sudo apt-get install qtparted**, so no comment on gprated sorry, it seems to work a treat.

Make certain to update the /etc/fstab file by the way. 

As an aside have you considered VMWare to run windows, my laptop is only a 1.8 core duo and even when it had 1gb of ram XP in VMWare felt native (no VMWare for gutsy yet though, unless I am missing something).

---

### Post by x-point on 2007-09-12
> **redmonster13 said:**
> I am trying to unmount my secondary HDD so that I can reformat it and install windows on it. I have tried using the gparted live cd to do this but I cant get the graphical client to run and I am not confident enough with the command line to do it that way.

The secondary hdd is located at /media/sdb1 and I have tried

sudo unmount /media/sdb1 

the result was command unknown unmount
(or something to that effect)


any help I can get with formating this drive to ntfs would be greatly appreciated.

Just try *sudo umount -f /media/sdb1* instead of "unmount". To check if it's still mounted just type *mount* command that will show you all mounted filesystems. After it's unmounted you can use fdisk or gparted utilities to get that HDD partitioned. I prefer fdisk :)

---

