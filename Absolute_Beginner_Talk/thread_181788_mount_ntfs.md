---
title: "mount ntfs"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-24
yeah i know everybody asks this... ... but i followed the directions at ...
[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

and this is what i get..... for the output of ....

  sudo fdisk -l 
  cat /etc/fstab 
  mount | sort

jesus@jesus-am-teh-gae:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30023   241159716   83  Linux
/dev/sda2           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS
jesus@jesus-am-teh-gae:~$   cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/ntfs1 ntfs ro,nls=utf8,umask=0222 0 0
/dev/hdb1 /mnt/ntfs2 ntfs ro,nls=utf8,umask=0222 0 0
jesus@jesus-am-teh-gae:~$   mount | sort
/dev/hda1 on /mnt/ntfs1 type ntfs (ro,nls=utf8,umask=0222)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)
/dev/hdb1 on /mnt/ntfs2 type ntfs (ro,nls=utf8,umask=0222)
/dev/hdb1 on /tmp/disks-conf-hdb1 type ntfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
udev on /dev type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
varrun on /var/run type tmpfs (rw)

basically i still get the error that i dont have the permissions to view this disc.


i have a primary SATA drive thats been wiped out for ubuntu and 2 secondary IDE drives in my box currently both formatted with NTFS that i'd like to access.

any help would be appreciated. i'm really enjoying ubuntu so far i just hope i can figure out ways to do everything i need to do!

---

### Post by aysiu on 2006-05-24
I don't know if this makes a difference or not, but you might want to get the *ro* out of there: ```
/dev/hda1 /mnt/ntfs1 ntfs ro,nls=utf8,umask=0222 0 0
/dev/hdb1 /mnt/ntfs2 ntfs ro,nls=utf8,umask=0222 0 0
``` So maybe this instead? ```
/dev/hda1 /mnt/ntfs1 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /mnt/ntfs2 ntfs nls=utf8,umask=0222 0 0
``` You may also want to try mounting them to their own static directories outside of /mnt or /media: ```
/dev/hda1 /ntfs1 ntfs ro,nls=utf8,umask=0222 0 0
/dev/hdb1 /ntfs2 ntfs ro,nls=utf8,umask=0222 0 0
``` You'd have to make those directories first, of course, but I think you know how to do that.

Have you tried rebooting? ```
sudo mount -a
``` usually works, but sometimes a clean reboot fixes the mounted drives after you've modified the /etc/fstab.

---

### Post by sotonin on 2006-05-24
DURRRRRH ... i feel a little durh durrrrRh...

that did the trick.... the command wasn't enough but the reboot did it.

thanks, sorry for the noob problem. :P

---

