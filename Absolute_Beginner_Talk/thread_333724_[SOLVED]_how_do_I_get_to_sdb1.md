---
title: "[SOLVED] how do I get to sdb1"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-07
1.  I have added a new drive.
2.  It is formatted as ext3
3.  It is mounted as sdb1

How do I access this drive. Where will I find it to use it. This is a SATA drive so the adding it to fstab is considerably different. Where do I find the info to do this.



================================================
squrl@squrl-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14589   117186111   83  Linux

============================================
squrl@squrl-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /mnt/sdb1 type ext3 (rw)


Thanks to someone in advance. This has been an all day affair and It is almost the end of ubuntu for me.

---

### Post by taurus on 2007-01-07
```
cd /mnt/sdb1
ls -la
```

---

### Post by squrl on 2007-01-07
Hi Taurus,

Got there.  Now what does the string look like for fstab for an sata drive.

Thanks.  Wish I had 1% of your linux knowledge

---

### Post by taurus on 2007-01-07
Something like this in your /etc/fstab!

```
/dev/sdb1   /mnt/sdb1   ext3   defaults   0   1
```

---

### Post by squrl on 2007-01-07
Don't think so for a sata drive. It uses something called a UUID with a gazillion numbers


================================================
squrl@squrl-desktop:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26971987-3b36-4b6d-80af-9c8f78ed17bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2f03bf5b-c2e2-42d4-998a-b0145181f099 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
====================================================

Kinda like that only for sdb1

---

### Post by taurus on 2007-01-07
/dev/sdb1 is the old way while UUID is the new method from Edgy.  Personally, I always go with the /dev/sdb1 thing since it's easy to understand and especially if you keep changing your partition table.  Each time you resize, format, or move your partition around, the UUID would change but the /dev/sdb1 is always the same.

So either way is good.  ;)

---

### Post by squrl on 2007-01-07
Hey that will work as long as it works.   

Thanks a million Taurus.

---

### Post by taurus on 2007-01-07
That will work because I always use /dev/XXX on all my machines.

---

