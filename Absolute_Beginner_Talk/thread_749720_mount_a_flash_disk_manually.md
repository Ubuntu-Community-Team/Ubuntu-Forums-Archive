---
title: "mount a flash disk manually"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mosaab on 2008-04-08
Hello, where are the unmounted drives files in ubuntu?
how can I mount a flash manually .. because I have been trying ... actually it works when I plug the flash again automatically ... but I just want to know.

thanks

---

### Post by annda on 2008-04-08
hi,

just as with all the other accessible disks/drives/partitions

```
sudo fdisk -l
```

this will tell you the right device node (/dev/xxx). as to how you should mount them and all the options you need, consult

```
man mount
```

e.g. umask values for the FAT filesystem

---

### Post by Mosaab on 2008-04-09
this doesnt display the flash memories !

---

### Post by conscious on 2008-04-09
If you plug it via USB, use "lsusb" to get the list of connected devices. To actually mount a device, use "mount" or "pmount", which doesn't require admin rights.

---

### Post by Mosaab on 2008-04-09
now this is my question ... what would be the command ? mount what ?
like : mount dev/usb ?
and lsusb gives me an output I cannot understand! only a list of numbers...

---

### Post by conscious on 2008-04-10
Indeed, lsusb is not very helpful for this.

You can run "fdisk -l" or "sudo fdisk -l" to see the list of partitions, including the usb ones, just like annda says. To actually mount a partition, you run:
```
sudo mount *device mountpoint*
```
Or:
```
pmount *device*
```

For details, see the man pages.

---

### Post by Mosaab on 2008-04-14
Actually the fdisk shows only one partition .. and it doesnt show any USB storage devices.

---

### Post by Mosaab on 2008-04-14
ok maybe I wast clear, suppose I have a flash memory adn its mounted automaticly.
Q1. Where is it mounted by default in ubuntu?
Q2.Do all storage devices get mounted in the same place or node ?
Q3. if I unmount it by right clicking on the icon on the desktop and click unmount, and the flash name is "Mosab". what should I type to mount it manually (without taking the flash out and in again)

---

### Post by craetech on 2008-04-29
Hi Mosaab, I'll try to answer your questions. Please correct me if I'm wrong.

A1. /media/disk
A2. Yes, i.e. /media
A3. mount -t vfat /dev/sda1 /media/disk

For #3, mount in no way references the drive's name. I was actually looking for how to mount my flash drive manually (auto-mounting somehow failed), but seems lsusb "refreshed" the bus and auto-mounted for me.

Hope that helps.

---

### Post by hellonull on 2008-04-30
A few things...

1. You need to put sudo at the beginning of the line, as you need root privileges to run the mount command.

2. I doubt the block device is /dev/sda1, as sda1 is usually the first partition of a SATA hard drive. You have to open /dev and look around to find the name of the flash drive. I tried but couldn't find it for mine :\. I have manually mounted flash drives in FreeBSD using the same procedure but finding the correct device name appears to be a lot more difficult when using Ubuntu.

3. Assuming you find the correct device name, you can mount the flash drive to any directory that exists in the filesystem. If you want to mount it to a directory that does not exist, you have to create the directory first.

---

### Post by Mosaab on 2008-06-18
I got the answer:

sudo mount -t ntfs-3g -o force /dev/sdb1 /home/where you want to mount it..

Thank you anyway guys.

---

