---
title: "Portable usb disk"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-16
I've got an laptop hard drive conected to a usb adaptor.How do I mount it in Ubuntu 6.06.

---

### Post by JoeG on 2006-05-17
USB drives typically come up as scsi drives (i.e. **/dev/sda** ).  You'll want to mount the filesystem it contains to an empty folder.  

For example, I use:

**mount /dev/sda1 /media/usb**

to mount mine.  This is the first (and only) partition on my drive.  For a more permanent solution (assuming that yours comes up as /dev/sda and you only have one partition formatted FAT32) you could:

**mkdir /media/usb**

and add the following line to /etc/fstab:

**/dev/sda1       /media/usb      vfat    user,noauto     0       0**

Happy data accessing

JoeG

---

