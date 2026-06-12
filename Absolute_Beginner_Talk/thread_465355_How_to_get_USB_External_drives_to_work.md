---
title: "How to get USB External drives to work"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by drspastic on 2007-06-05
With either pen drive or my big 400Gb-ers I can't figure out how to access these.

Any ideas?

Thanks

---

### Post by kpkeerthi on 2007-06-05
What happens when you insert your USB drive? Are you not seeing an icon on your desktop? 

Insert your pend drive and post the output of ```
sudo fdisk -l
``` and ```
sudo mount
```

---

### Post by drspastic on 2007-06-05
fdisk shows just the two internal driveS.

Second command rendered the following:-

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4810    38636293+  83  Linux
/dev/hdc2            4811        4998     1510110    5  Extended
/dev/hdc5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         509     4088511   82  Linux swap / Solaris
/dev/hdd2             510       48641   386620290    5  Extended
/dev/hdd5             510       48641   386620258+  83  Linux
ed@ed-desktop:~$ sudo mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

