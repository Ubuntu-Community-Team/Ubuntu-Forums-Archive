---
title: "Formatting Ext3"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-04-08
Anyone have a link for a good guide on formatting a drive to ext3 file system?

---

### Post by Happy_Man on 2007-04-08
Get the GParted LiveCD and use that. Or maybe the GParted on the Ubuntu LiveCD. Anything will do, really.

---

### Post by Najand on 2007-04-08
parted and gparted are GNU powerful partition editors. gparted is easier to use for newbies and it has almost the same features as parted. It is available in the live CD as a pre-installed package.
The official guide can help you how to use it:[URL="http://gparted.sourceforge.net/larry/generalities/gparted.htm"]
http://gparted.sourceforge.net/larry/generalities/gparted.htm[/URL]
Note that, bacuse it has been already installed, you can skip the first part concerning installation and setup.

---

### Post by dreadh3ad on 2007-04-08
So how do I mount the partition once I have created it?

---

### Post by Najand on 2007-04-08
Use (let us assume your device name is /dev/sda6):
```

sudo mkdir /media/FOO
sudo mount -t ext3 /dev/sda6 /media/FOO

```
Use the device name you used to format or used:
```

sudo fdisk -l

```
to see your partitions devices.
If you could do that you can add it to /etc/fstab to be able to mount patitions easier.

---

### Post by dreadh3ad on 2007-04-08
Do i need to do this each time i reboot?  Im using this drive for ubuntu and Xp giving them both read and write cabilities.  basicly to share music and such.

---

### Post by Najand on 2007-04-08
Did it work?
Actually for sharing music and files between Linux and Windows it is better to use FAT32 filesystem. However if you can mount them in winodws there is no problem with that.

---

### Post by dreadh3ad on 2007-04-08
Yes it did, but the mount is read only.  I need the ability to write as well.

---

### Post by Najand on 2007-04-08
OK. open a terminal and type:
```

$ gksu gedit /etc/fstab

```
Then add the following details in a new line (all sections must be separated by single tabs):
```

DEVICE_NAME    MOUNT_POINT    ext3     defaults,users,auto,rw    0    2

```
Change DEVICE_NAME and MOUNT_POINT with proper values.
Then restart your computer and see if it works.

---

### Post by dreadh3ad on 2007-04-08
Its mounted but i still cannot write to it

whoracle@TOOL:~$ gksu gedit /etc/fstab

(gedit:7384): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

then the file opens and heres what i have:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/mount	ext3	defaults,users,auto,rw	0	2

```

---

