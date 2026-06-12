---
title: "Mounting"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by rclimb514 on 2005-09-15
I've just recently installed Ubuntu, after using Fedora for about a year.  I have 2 HDs and I installed the new distro over my old Windows partition (finally got rid of that mess once and for all) while my old Fedora was on the other disk.  However, I'd like to mount my Fedora partition into my new filesystem, to make transferring my old data a bit easier.  When I try to do the mount, I get the error 

```
mount: /dev/hdb2 already mounted or /mnt/fedora busy
```

I think its pretty unlikely that /mnt/fedora is in fact busy, as it was just created, and I can't imagine how hdb2 would already be mounted.  Its not listed in mtab, anyways.  Incidentally I have no problems mounting hdb1, which is another partition for the old fedora system.

Thanks
rclimb514

---

### Post by evilghost on 2005-09-15
You mounting as sudo/root?

---

### Post by mlomker on 2005-09-15
What is the output of these?

```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by rclimb514 on 2005-09-16
Yeah, I'm working from root.

Output:

$ fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14       14593   117113850   8e  Linux LVM

$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks

---

### Post by mlomker on 2005-09-17
> 
/dev/hdb2              14       14593   117113850   8e  Linux LVM


I thought that LVM was the linux version of software RAID.  Do you have mirroring or RAID set up?  Do you know what type of filesystem it has on it?

Could you approach it from the other angle and mount the Ubuntu drive from Fedora and copy in that direction?  I know that's not a solution but a work-around...

---

### Post by rclimb514 on 2005-09-19
I was able to boot in Fedora and mount from there.  Thanks for the help.

---

