---
title: "Partition woes Pendrive Linux"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Dustin_Bowls on 2008-03-16
I installed Ubuntu 7.1 on a 4 gig flash drive via the instructions on pendrives website here:


[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and here

[http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/](http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/)

Now for some reason I dont have access to the larger of the two partitions, when I do an fdisk -l here is the result:

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          92      738958+   6  FAT16
/dev/sdb2              93         491     3204967+  83  Linux

When I open the device with gparted I see the following

Partition                     Filesystem                 Mountpoint            Size                  Used
/dev/sdb1                   fat16                         /cdrom                 721.64 MiB        668.51
/dev/sdb2                   ext2                          /cow                     3.06GiB             ---

if I click on sdb2 I get an unmount option, but an error that says /cow not found and I can't seem to do anything with it.  Gparted and fdisk are the only utilities that even see the partition.  

Is there a way to redo the second partition and make it usable without messing up the 1st one?

---

### Post by Nikhil Gohil on 2008-03-16
you probably need to seta mount point for sdb2.
```
sudo mount /dev/sdb1 mounpoint
```
replace mountpoint with any folder u have created, eg 
```
sudo mount /dev/sdb3 /media/disk2
```

---

