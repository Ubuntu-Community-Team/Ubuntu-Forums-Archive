---
title: "Feisty not reading usb drive"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Rylin on 2007-09-03
My usb drive was working fine last night but today the system won't even pick up the device when I plug it in. Is there a command to manually check for mounts and possibly unmount and mount the drive again?

Thanks

---

### Post by taurus on 2007-09-03
Check to see if the system even detects it first.

```
sudo fdisk -l
```

---

### Post by Rylin on 2007-09-03
This is what it displayed back:

alien@alien-laptop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Rylin on 2007-09-03
Any suggestions? :???:

---

### Post by taurus on 2007-09-03
That would be lower case letter L, not number 1.

```
sudo fdisk -**l**
```

---

### Post by Rylin on 2007-09-03
ah ok, that worked. :)

This is what it displayed:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS


Its the 120gb drive and it looks like it does see the external usb drive..just not able to use it.

---

### Post by taurus on 2007-09-03
```
sudo aptitude update
sudo aptitude install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Rylin on 2007-09-03
I get this option when i ran the 2nd to last command:

Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0


Should I just restart using ctrl-alt-backspace?

---

### Post by taurus on 2007-09-03
You need to boot into Windows and unmount your USB drive cleanly instead of just unplugging it or powering it down.  Then, insert it and unmount it again.  Now, see if you can read it in Ubuntu.

---

### Post by Rylin on 2007-09-03
Ok i plugged it into windows machine and safely removed it from the computer. Then plugged it into ubuntu machine and it still didnt recognize it. I was able to get it to recognize it by forcing it to mount but it didnt show any of my files. 

Any other ideas to get it to pick up the usb drive?

---

### Post by taurus on 2007-09-03
What's the output of this command then?

```
ls -la /media/sdb1
```

---

### Post by Rylin on 2007-09-03
Ah, with that command i was able to see my files. :)

Now I just need to know how to access them normally.

---

### Post by taurus on 2007-09-03
What do you have in mind?  Do you want to copy some files from /media/sdb1 to your $HOME directory?  See if you can see those files with nautilus.

```
nautilus /media/sdb1
```

---

### Post by Rylin on 2007-09-03
Ok that was really weird

```
ls -la /media/sdb1
```

That must have done something, because now it recognized it and I have an icon on the desktop to the drive. :confused::)

I'll have to save alot of the code you gave me in case this happens again. Really appreciate all the help.

-Rylin

---

### Post by taurus on 2007-09-03
One more code which you need to know.  You need to _unmount_ it first before you unplug it from your machine or you could damage the drive or destroy the files on it.

```
sudo umount /media/sdb1
```

Basically, the only thing you need to mount is how to mount it and unmount it.

To mount:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
To unmount:
```
sudo umount /media/sdb1
```

---

