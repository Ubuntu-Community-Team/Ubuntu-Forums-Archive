---
title: "Could I move my entire partition?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Narpas on 2006-07-25
I want to move my entire Linux partition, as it is now, onto a different space on my drive. It's an ext3 partition, has everything on it except swap, and I would like to be able to, later, re-install Grub and use it again.

Is this possible or reasonable?

---

### Post by ubuntuuser on 2006-07-25
It is possible, I have already done this. Just be sure to adapt /boot/grub/menu.lst and your fstab file. And if something goes wrong, be sure to have a backup of all important data, and a live-cd of your choice to access the drive, just in case. Good luck.:) Instead of changing menu.lst, you could also boot from a livecd, chroot to your new drive, and reconfigure grub.
 ```
mount /dev/hdaNEW /mnt/drive
chroot /mnt/drive /bin/bash
grub-install
reboot
```

---

### Post by Narpas on 2006-07-25
Thank you. So, it basicly boils down to:

* Move all of the files to a second partition, retaining hiarchy, of course.
* Make Grub figure itself out

Zat all?

---

### Post by john_spiral on 2006-07-25
As far as I know, you will only need to edit the following (please get some more input on this):

/boot/grub/menu.lst

use: Tells grub where to find O.S

/boot/grub/device.map

use: hard drive number assignment, this won't change if you keep linux on the same drive. 

e.g (2 sata drives connected to a machine) 

(hd0) /dev/sda
(hd1) /dev/sdb

/etc/fstab

use: file system mount points, change according to new location of linux partition

remember to use the **sudo fdisk -l** command to find partition/disc layout

---

### Post by djsroknrol on 2006-07-25
I've done it with the help of partimage...I moved my whole hda2 to my 2nd HD, rearranged things, resized partitions and them moved my hda2 partition back with no problems at all. 

The program worked great for me. Google for it..it might be your answer..

---

### Post by aysiu on 2006-07-25
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

