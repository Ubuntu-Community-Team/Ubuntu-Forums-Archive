---
title: "formatting usb flash drive"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-04
I just installed Ubuntu 6.06 and would like to format my new usb flash drive. How can I go about this? I tried going to system->administration->disks but it would not let me format it this way. 

Also, how can I go about changing the usb flash label? It says USB DISK each time I mount it, how can I change it to something else? Sorry, I am new to linux.

Erick

---

### Post by mcduck on 2006-08-04
> **emprog said:**
> I just installed Ubuntu 6.06 and would like to format my new usb flash drive. How can I go about this? I tried going to system->administration->disks but it would not let me format it this way. 

Also, how can I go about changing the usb flash label? It says USB DISK each time I mount it, how can I change it to something else? Sorry, I am new to linux.

Erick

You can't format a drive that is mounted. You have to either unmount it first, or disable automounting for USB drives before you plug the drive in.

When it's not mounted you should be able to format it with the Disks tool :)

---

### Post by pistcivet on 2006-08-04
I've always liked the command line:
sudo mkdosfs -c -F 16 -n VOLUMELABEL /dev/sda1

If you have a SATA drive, /dev/sda1 may not be correct.
(it wouldn't be good to format you're hard drive by accident)

man mkdosfs
for more info. :)

---

### Post by emprog on 2006-08-04
Thanks for the help, when I unmount the device (while leaving it attached) the format option goes away in disks and it states that there are no known partitions.

Erick

---

### Post by petersjm on 2006-08-04
I'm not sure, so don't quote me, but would gParted recognise the flash drive? Then you could format the disk through that.

---

