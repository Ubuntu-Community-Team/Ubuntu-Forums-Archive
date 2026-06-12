---
title: "Help mounting new DVD player"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by adam s on 2007-03-24
Hi,

I have just bought a new DVD-RW player.

I have installed it into my tower, added the bus cable (There was a spare connector on the cable that was attached to my existing DVD-R) and added the power cable.

When I re-booted my computer, the new DVD player definitely has power.

If I do an ls /dev/hd* I get the following  :


adam@frodo:/dev$ ls -l hd*
brw-rw---- 1 root disk   3,  0 2007-03-24 22:14 hda
brw-rw---- 1 root disk   3,  1 2007-03-24 22:14 hda1
brw-rw---- 1 root disk   3,  2 2007-03-24 22:14 hda2
brw-rw---- 1 root disk   3,  5 2007-03-24 22:14 hda5
brw-rw---- 1 root disk   3, 64 2007-03-24 22:14 hdb
brw-rw---- 1 root disk   3, 65 2007-03-24 22:14 hdb1
brw-rw---- 1 root disk   3, 66 2007-03-24 22:14 hdb2
brw-rw---- 1 root disk   3, 69 2007-03-24 22:14 hdb5
brw-rw---- 1 root cdrom 22,  0 2007-03-24 22:14 hdc

If I run a sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4680    37592068+  83  Linux
/dev/hda2            4681        4865     1486012+   5  Extended
/dev/hda5            4681        4865     1485981   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4824    38748748+  83  Linux
/dev/hdb2            4825        4870      369495    5  Extended
/dev/hdb5            4825        4870      369463+  82  Linux swap / Solaris


and below is the current contents of my /etc/fstab file :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /hd-slave       ext3    defaults        0       0


Where do I find the name of the device to mount?

Thanks in advance for your help,

Adam.

---

### Post by jeffathehutt on 2007-03-24
I'm not quite sure of your setup.  Do you mean you installed the new DVD-RW and left the old drive still connected, or did you replace the existing drive with the new one?

If you have both of them connected at the same time, make sure you set the jumpers on the new drive to slave.  Once you get linux to detect the new drive, type:
```
sudo mkdir /media/dvdrw
```
then all you need to do is add an entry in /etc/fstab like this:
```
/dev/hdd /media/dvdrw udf,iso9660 user,noauto 0 0
```

---

### Post by adam s on 2007-03-25
Thanks,

I have left the old DVD player in - and I haven't set the new DVD to slave.

I will give this a go when my son goes to sleep.....

Thanks,

Adam.

---

