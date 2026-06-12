---
title: "making a bootable clone?"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by loksipan on 2005-10-07
Could I install ubuntu on a spare HDD in an external USB enclosure, then copy everything under root from my main internal drive to the usb drive (with overwrite) to create an (almost?) identical bootable copy?

I can see two problems:-

1) Even as root I will not be able to overwrite some files/folders already existing on the target clone drive due to permissions.

2) If the external clone drive is under /media/usbdisk/  then copying everything under root from the source drive will automatically include everything from the target drive as well which might become a never-ending task.

Loksipan

---

### Post by az on 2005-10-07
[QUOTE=loksipan]
1) Even as root I will not be able to overwrite some files/folders already existing on the target clone drive due to permissions.

2) If the external clone drive is under /media/usbdisk/  then copying everything under root from the source drive will automatically include everything from the target drive as well which might become a never-ending task.

Loksipan[/QUOTE]

1.  No, you will be able to overwrite them as root.

2.  You could either just use partimage, to make an image of your partition or just do it by hand.  

-Boot into the installer and let it autodetect everything. (Let it get to the partitioner)
-CTRL-ALT-F2
-Plug in your usb drive.
-make sure that there is a partition on your usb drive that is of the appropriate size.
-(assuming you are using /dev/sda1 as your usb drive) dd if=/dev/hda5 of=/dev/sda1
-mount the usb partition and edit fstab accordingly.
mkdir /usb
mount /dev/sda1 /udb
vi /usb/etc/fstab
(or use nano)

---

