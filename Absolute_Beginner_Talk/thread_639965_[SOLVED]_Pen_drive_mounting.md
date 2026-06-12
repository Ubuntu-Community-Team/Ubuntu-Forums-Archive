---
title: "[SOLVED] Pen drive mounting"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-13
I am trying to access pen drive from terminal. what is the path to my pen drive? When I type "sudo fdisk -l", it shows a device at /dev/sdb1  I assume that this is where my pen drive is mounted, however when I try to cd into by typing cd /dev/sdb1, I receive an error. Can someone tell me what I am doing wrong?

---

### Post by taurus on 2007-12-13
Nope.  It has not been mounted until you mount it.  Assuming it's fat32 filesystem, run

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
Now, you can access your pen drive from /media/sdb1.  Don't forget to unmount it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by annda on 2007-12-13
assuming it is mounted, it is probably at /media/disk or something similar.

use the mount command to see whether and where it is mounted.

---

### Post by bodhi.zazen on 2007-12-13
> **fmbugdadi said:**
> I am trying to access pen drive from terminal. what is the path to my pen drive? When I type "sudo fdisk -l", it shows a device at /dev/sdb1  I assume that this is where my pen drive is mounted, however when I try to cd into by typing cd /dev/sdb1, I receive an error. Can someone tell me what I am doing wrong?

the /dev/sdb1 is the raw device and is accessed by the kernel at a low level.

In order to access it the device you need to "prep" it for use or mount it.

Many times removable devices will auto mount in /media

such as /media/sdba or /media/disk or /media/$LABEL if you have set a label.

If it does not auto mount you can use pmount or mount.

taurus showed you how to use mount. To use pmount :

pmount <device> <mount_point>

The differnece is, pmount assumes /media so you leave that out.

```
pmount /dev/sdb1 disk
```

Will mount the device at /media/disk

pmount works with removable devices but can be configured to work with fixed disks.

You can also add an entry to fstab. If the device is defined in fstab, the mount comand is shortedned to either :

```
mount /dev/sdb1 #Just the device
mount /media/disk #Just the mount point
```

How to fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by fmbugdadi on 2007-12-13
Thanks for the information guys. I was able to successfully mount my pen drive.

---

