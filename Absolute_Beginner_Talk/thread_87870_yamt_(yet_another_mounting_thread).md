---
title: "yamt (yet another mounting thread)"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by quintok on 2005-11-09
well I tried, I really did but there's only so many places a newbie can look before they start getting frustrated.  here's my info:

problem:
/dev/hda1 not mounting.
error from 'mount': /dev/hda1 already mounted or /media/windows busy
'noauto' is the only possible exception for the error, it does not come up straight away from mount but I assume this is because noauto mounts on attempting to access

fstab:
> proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222	0       0

fdisk -l:
> Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2310    18555043+  83  Linux
/dev/hdb2            2311        2482     1381590    5  Extended
/dev/hdb5            2311        2482     1381558+  82  Linux swap / Solaris

mount:
> /dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

I have tried these configurations:
rw,user,noauto
user,noauto
user,noauto,nls=utf8
default

any help greatly apreciated, thanks :)

---

### Post by Pablo_Escobar on 2005-11-09
It looks allright.
Just a wild shot, try to change the "windows" entry to other like "drive_c". 
"sudo mkdir /media/drive_c"
"sudo mount -a"

Maybe this will clear something up.

---

### Post by quintok on 2005-11-09
Hi Pablo,
I tried doing as you said, I did change fstab so that it said:
/dev/hda1       /media/drive_c  ntfs    nls=utf8,umask=0222	0       0
still came up with the same error.  I'm running a custom kernel but it has ntfs support (module), I ran lsmod and it was there though .

---

### Post by Pablo_Escobar on 2005-11-09
Then I'd say domething went wrong with the kernel You've compiled.
I'm no kernel build expert so it tough for me to judge.
As I see it, Your fstab looks allright. You have setup directories allright. It should work. Then something must be with Your kernel. Try to boot the generic one and see if hda1 mounts.

---

### Post by quintok on 2005-11-09
it seems unlikely, I was having the same issue on the same kernel and I did not change anything about ide/file systems etc.  I followed the vanilla kernel update in 'Customization Tips & Tricks' to the letter

---

### Post by quintok on 2005-11-09
does anyone have any suggestions on where else I should look?
thanks.

---

### Post by trash on 2005-11-09
Here ya go...

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

---

### Post by quintok on 2005-11-09
Thanks trash,
unfortunetly I did follow that and it still came up with the same error.  I have mounted this drive (although not specifically this format as I'd formatted between linux attempts) before using ubuntu and the FAQ, it seems silly something has changed.

---

### Post by trash on 2005-11-09
sorry it didn't help, I only tried the vfat because my shared partition is fat32

---

### Post by gord on 2005-11-09
have you tryed loading up a live cd of whatever version of ubuntu your using and mouting it in that? if you can do it fine in there then its pritty likely that youv messed something up with your custom kernel

---

