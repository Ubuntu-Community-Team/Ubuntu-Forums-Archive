---
title: "fstab question"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-17
acoording to dmseg the external cd/dvd  writerhas been detected . it has a usb connection. i have a labtop and the internal cd/dvd is not working
hence the external situation.

fstab looks like this do i need to amend it to take into account the external usb dvd/cd writer?


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by wahman143 on 2006-07-17
Hi,
If your writer is USB, then it's going to be housed as a "SCSI" device (ie - it will use /dev/sdx as opposed to /dev/hdx).  So you need to determine where it is - if you are not using any other SCSI or SATA devices, then it will probably be /dev/sda or /dev/sda1.  If you ARE using any SCSI or SATA devices, it will be the last one in the chain.

Assuming you're not using any other SCSI/SATA devices, this is how it should look in fstab:

```

/dev/sda  /your/mount_point  auto  user,noauto,ro  0 0

```

Hope that helps,
W.

---

