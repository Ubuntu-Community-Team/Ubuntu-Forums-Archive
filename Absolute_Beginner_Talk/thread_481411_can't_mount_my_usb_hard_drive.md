---
title: "can't mount my usb hard drive"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mkeithcloud on 2007-06-22
Hey I am new to ubuntu and I have a seagate 80gb usb hard drive that I can't use. When I plug it in it doesn't automount, at least not to the desktop and when I do an fdisk -l I get this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)

so I guess that means that ubuntu recognizes it...but I can't access it. Please help!!

---

### Post by stijngysemans on 2007-06-22
what you can do is manually mount the harddrive
```

#create directory
sudo mkdir /media/myHD
#manualy mount it
sudo mount /dev/sdb /media/myHD

```

---

### Post by logos34 on 2007-06-22
if you on feisty, it's usually pretty good about automounting usb:

gnome-volume-properties

On the first tab (storage), make sure the first three boxes for removable drives are ticked.

When it shows up on your desktop, right-click on the icon and choose properties.  Verify you have write permission.

---

### Post by mkeithcloud on 2007-06-22
I made sure those boxes were ticked. When I tried those lines it came back wit this:

root@pkiflptmrk:~# sudo mkdir /media/myHD
root@pkiflptmrk:~# sudo mount /dev/sdb /media/myHD
mount: you must specify the filesystem type

Also, dumb question, how can you tell if it's feisty or something else?

---

### Post by logos34 on 2007-06-22
try 
**sudo mount -t vfat /dev/sdb1 /media/myHD**


info:

**uname -r**  (or -a)
**lsb_release -a**

---

### Post by mkeithcloud on 2007-06-22
that worked.. thanks for all your help guys!!

---

