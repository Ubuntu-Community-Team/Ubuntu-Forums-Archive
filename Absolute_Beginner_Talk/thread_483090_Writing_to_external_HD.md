---
title: "Writing to external HD"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2007-06-24
Hi,

First off -- I have read [_this_]("http://ubuntuforums.org/showthread.php?t=344326&page=3") to no avail, just in case I get pointed in that direction.

I can't seem to write to my external hard drive.  This is not a hardware issue as I can write files to the disk in Windows fine.

FYI, *mount* gives:

```

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/seadisk type ntfs (rw,noexec,nodev,umask=0000,utf8)
```

And *fdisk -l* gives:

```

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS
```

I also did a *dmesg* before and after the drive is connected, then *diff*'d the two results, which resulted in:

```

431a432,449
> [  299.100000] usb 4-5: new high speed USB device using ehci_hcd and address 3
> [  299.232000] usb 4-5: configuration #1 chosen from 1 choice
> [  299.232000] scsi3 : SCSI emulation for USB Mass Storage devices
> [  299.232000] usb-storage: device found at 3
> [  299.232000] usb-storage: waiting for device to settle before scanning
> [  304.232000] usb-storage: device scan complete
> [  304.232000] scsi 3:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
> [  304.236000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
> [  304.236000] sdb: Write Protect is off
> [  304.236000] sdb: Mode Sense: 27 00 00 00
> [  304.236000] sdb: assuming drive cache: write through
> [  304.240000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
> [  304.240000] sdb: Write Protect is off
> [  304.240000] sdb: Mode Sense: 27 00 00 00
> [  304.240000] sdb: assuming drive cache: write through
> [  304.240000]  sdb: sdb1
> [  304.272000] sd 3:0:0:0: Attached scsi disk sdb
> [  304.272000] sd 3:0:0:0: Attached scsi generic sg1 type 0
```

I can view files fine, but (obviously) want to be able to write files.

I have tried all manner of combinations in */etc/fstab* and each time I get told I can't write files to the disk.

Can anyone help?

Regards.

---

### Post by ugm6hr on 2007-06-24
Have you installed ntfs-3g?

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Important bit:
```
sudo apt-get install ntfs-config
```

---

### Post by Zzl1xndd on 2007-06-24
what format is the Drive in is it Fat32, Ext3, NTFS?

(oh well ugm6hr beat me to the punch)

---

### Post by NegativeSpace on 2007-06-24
tweakedenigma, ugm6hr: thanks, that's sorted the problem!

---

