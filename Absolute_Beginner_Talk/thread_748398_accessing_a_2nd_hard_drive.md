---
title: "accessing a 2nd hard drive"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-04-07
hi, i have been using Fluxbuntu for about a month & a half now, and am enjoying it just fine. the problem i'm having is that i installed it on an old Dell Dimension desktop that was previously running Windows 2000. prior to install Fluxbuntu on the machine i was using a secondary drive to store my music and family pictures. well after installing Fluxbuntu i've found that the OS finds the device, but i'm unable to mount it to my file system. the hard drive can be found at /dev/disk/by-id/ata-ST340016A_3HSAFFZS, but that's the only place the hard drive shows up. so if anyone could help me somehow access the hard drive so that i can back up my files it would be greatly appreciated, thanx

---

### Post by Michael.Godawski on 2008-04-07
Can you please post the output of these terminal commands?

```
mount
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Duck2006 on 2008-04-07
Some reading on mounting drives.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rockerphil on 2008-04-07
phil@phil:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
/dev/sdd1 on /media/usbdisk-1 type vfat (ro,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
/dev/sde1 on /media/usbdisk-2 type vfat (ro,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
/dev/sdf1 on /media/usbdisk-3 type vfat (ro,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
/dev/sdg1 on /media/usbdisk-4 type vfat (ro,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
/dev/sdh1 on /media/usbdisk-5 type vfat (ro,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,fmask=0177,dmask=0077)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)

phil@phil:~$ sudo fdisk -l

Disk /dev/sda: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12448551

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         868     6972178+  83  Linux
/dev/sda2             869         913      361462+   5  Extended
/dev/sda5             869         913      361431   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe26ae26a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           3       24066   bc  Unknown
/dev/sdb2   *           4        4865    39054015    7  HPFS/NTFS



phil@phil:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d4f00285-45a7-4fcb-9fab-4036c7c9f981 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7afb3395-ae3c-4546-b4c3-70e2f220d022 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



there ya go man, hope it'll help ya help me

---

### Post by fenian on 2008-04-07
Try this...
First make a mount point for the drive....

> sudo mkdir /media/windows

Next edit the fstab file so the disk automounts...

> sudo gedit /etc/fstab

change the file so it looks like this...

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=d4f00285-45a7-4fcb-9fab-4036c7c9f981 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=7afb3395-ae3c-4546-b4c3-70e2f220d022 none swap sw 0 0
/dev/sdb2 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

(Basically you just added the line  '/dev/sdb2 /media/windows ntfs nls=utf8,umask=0222 0 0')

Next mount the drives...

> sudo mount -a


You can then enable read/write support by following the instructions[ here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

