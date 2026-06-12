---
title: "ext3 external usb disk volume names"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-09-20
I have 2 external usb disks. Yesterday I formatted these to ext3 and now have the following issue; the name of the mount directory depends on which disk is mounted first (the first mounted disk will be '/media/usbdisk' and the second '/media/usbdisk-1'. When the disks were FAT formatted they had a volume name wich was used in the mount directory (e.g. '/media/lacie' and '/media/lacie_backup'), I could always see on which disk I was. 

Is it possible to assign a 'mount' name to an ext3 formatted disk (without manually mounting it, but upon attaching the disk)?

---

### Post by monktbd on 2006-09-20
yes it is possible.

the command on the terminal is
> sudo  e2label /dev/sda1 myname 
to give the name myname to the harddisk partition /dev/sda1.

to know what you need to use for /dev/sda1 just make a quick

> cat /etc/mtab

while the harddisk is mounted.

---

### Post by lorre on 2006-09-20
Thanks, will try.

---

### Post by lorre on 2006-09-20
Works like charm.

---

