---
title: "Merging and formatting two consecutive harddrive partitions"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by MoxJet on 2006-06-05
I have two partitions on my 230gb-harddrive that I want to merge and format. They are /dev/sda5 and /dev/sda6. The computer is using ubuntu and I guess I want them to be vfat so I can reach them from both linux and windows. How would I do this?

---

### Post by anaconda on 2006-06-05
you can delete both partitions and then make a new partition, which is as big as both of the old ones together.

exept if one is primary partition and the other is extended partition. then it is a little more complicated.

PS: you might consider using ext3 instead of fat32 (vfat). By installing this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
you have full access to ext2/ext3 filesystems from windows!!!

---

### Post by MoxJet on 2006-06-05
Ok ext3 it is, but, how do I most eaisly format using ubuntu? Using disks or some terminal command?

---

### Post by anaconda on 2006-06-05
This isn't the easiest way, but it is how I am used to do it..

from command line (terminal):

sudo su
to get root rights

cfdisk  /dev/hda
Delete partitions that you want to destroy, and create new partition (with cfdisk)

mke2fs -j /dev/hda5
this formats partition hda5 to be of type ext3 (without the -j it would format it to be ext2) With mkfs you can format partition to be vfat if you prefer it. Just make sure that the partition you format is the new partition...

Notice that the numbering of the rest of your partitions (if you have them) change when you do this. eg. hda7->hda6  hda8->hda7 etc...  so you might want to edit your etc/fstab file accordingly.

I am sure that there is a graphical tool for partitioning & formatting disks in ubuntu. But because I am currently running xubuntu I dont remember its name. In xubuntu it is at /system/disks/partitions, and it has to be run as root if you want to make any changes...

---

### Post by bruenig on 2006-06-05
easiest way to do it (graphally)
```
sudo apt-get install gparted
```
go into gparted which would be located at System>Administratio>Gnome Partition Editor

Delete the two partitions, Make a new partition of the unformatted space and make it fat32 or ext3 if you want to use that driver, I personally like doing something that I know is supported by default on both systems (fat32).

---

