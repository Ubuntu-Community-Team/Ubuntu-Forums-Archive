---
title: "Need help with pen drive, please."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-04
When I was trying to install Gutsy from a Live CD it appeared that I had the option to load it onto my pen drive (4GB)

As the process began, it didn't get very far before there was an error message saying something to the effect that ' it couldn't install the file system ', or words to that effect.

I terminated the installation and now, when using Gutsy that is loaded to my hard drive, the pen drive icon doesn't show up on my desktop.

In Terminal I typed ' fdisk -l ' and got this:-

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002438

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 4244 MB, 4244636160 bytes
255 heads, 63 sectors/track, 516 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux
/dev/sda2             487         516      240975    5  Extended

Is there something I can do to make the pen drive show up, or have I made a BIG screw up here?

---

### Post by philinux on 2007-12-04
If you're trying to run it from a pen drive then you need this,

[http://pendrivelinux.com/](http://pendrivelinux.com/)

---

### Post by g2g591 on 2007-12-04
your pen drive is showing up, as /dev/sda "Disk /dev/sda: 4244 MB, 4244636160 bytes" it seems you have two partations on it, one regular partation (which you should be able to mount using a command like "sudo mount -t ext3 /dev/sda1 /pathto/your/mountpoint ") and an extended partation which isn't really a partaiton, you use extended patations to have more than 4 partations

---

### Post by tech9 on 2007-12-04
> **g2g591 said:**
> your pen drive is showing up, as /dev/sda "Disk /dev/sda: 4244 MB, 4244636160 bytes" it seems you have two partations on it, one regular partation (which you should be able to mount using a command like "sudo mount -t ext3 /dev/sda1 /pathto/your/mountpoint ") and an extended partation which isn't really a partaiton, you use extended patations to have more than 4 partations

this correct also, see this link...
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by L Campbell on 2007-12-04
> **tech9 said:**
> this correct also, see this link...
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

OK, thanks, I'm now trying to follow this method and this is what happens:-

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002438

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 4244 MB, 4244636160 bytes
255 heads, 63 sectors/track, 516 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux
/dev/sda2             487         516      240975    5  Extended
root@ubuntu:/home/ubuntu# umount /dev/sda1
umount: /dev/sda1: not mounted
root@ubuntu:/home/ubuntu# fdisk /dev/sda
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sda: 4244 MB, 4244636160 bytes
255 heads, 63 sectors/track, 516 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux
/dev/sda2             487         516      240975    5  Extended

Command (m for help): d
Partition number (1-5): p
Partition number (1-5): d
Partition number (1-5): p
Partition number (1-5): d
Partition number (1-5):

It seems that I get to #7 of the instruction list, then progress just ceases and it starts repeating.

---

### Post by tech9 on 2007-12-04
> **L Campbell said:**
> OK, thanks, I'm now trying to follow this method and this is what happens:-


Command (m for help): d
Partition number (1-5): p
Partition number (1-5): d
Partition number (1-5): p
Partition number (1-5): d
Partition number (1-5):

It seems that I get to #7 of the instruction list, then progress just ceases and it starts repeating.

your welcome! :)

for the partition number it's asking you to enter a number...
for the first one type 1 enter and for the second one type 2 enter ect.

---

