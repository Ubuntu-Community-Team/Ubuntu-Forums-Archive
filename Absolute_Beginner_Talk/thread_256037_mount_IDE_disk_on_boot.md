---
title: "mount IDE disk on boot"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by kditty on 2006-09-12
hi, i am having a problem with my second hard drive mounting. i can access it with root rights, and it shows up in sys>administration>disks, but i can not enable it or browse it there. the drive is in and working it seems but i can not get it to mount at all. id like for the drive to mount when i boot linux. here is the results of my ftab, mtab and fdisk -l. sys>administration>disks lists the drive as ext3 but fdisk -l lists it as ntfs. any suggestions? the drive i need is hdd, on partition 1.


---FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1 /media/storage ext3  umask=0222 0 0


---MTAB

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


---fdisk -l

Disk /dev/hda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19170   153982993+  83  Linux
/dev/hda2           19171       19452     2265165    5  Extended
/dev/hda5           19171       19452     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15504   117210208+   7  HPFS/NTFS

---

### Post by taurus on 2006-09-12
Change the last line in your /etc/fstab to 

```

/dev/hdd1 /media/storage ext3 defaults 0  2

```
Then, use chmod to set permissions for /media/storage!!!  Now, is it ext3 or NTFS???

---

### Post by kditty on 2006-09-12
i changed the last line in fstab to /dev/hdd1 /media/storage ext3 defaults 0  2 but i am not familiar with chmod, how do i go about changing the permissions with that?

---

