---
title: "Can't mount FAT32 external HDD"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Captainm on 2007-04-14
Hello,

I can't for the live of me figure out how to mount my external usb harddisk. For some reason it isn't mounted automatically. Here is my /etc/fstab (bolded the relevant part:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=26bb4a20-bbdb-40b5-aaad-29ac20fd5b83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7C7814E57814A046 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d47f5c26-ab46-f699-3290-438638525103 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/sda3       /media/IOMEGA_HDD vfat   noauto,owner,kuzu 0       0**
```

I created the /media/IOMEGA_HDD directory. Now when I try to mount the damn thing using sudo mount /dev/sda3 it give me the error message > mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Could anyone tell me what I'm overlooking here or point me in the right direction?

---

### Post by freebird54 on 2007-04-14
Can't say for sure what is happening there.  It LOOKS like you are trying to mount a partition, not a drive.  If it is a separate device, it won't also be sda# it'll be sdb#...

Could you clarify what you are attempting?

---

### Post by taurus on 2007-04-14
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by cvmostert on 2007-04-14
> **Captainm said:**
> Hello,

I can't for the live of me figure out how to mount my external usb harddisk. For some reason it isn't mounted automatically. Here is my /etc/fstab (bolded the relevant part:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=26bb4a20-bbdb-40b5-aaad-29ac20fd5b83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7C7814E57814A046 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d47f5c26-ab46-f699-3290-438638525103 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/sda3       /media/IOMEGA_HDD vfat   noauto,owner,kuzu 0       0**
```

I created the /media/IOMEGA_HDD directory. Now when I try to mount the damn thing using sudo mount /dev/sda3 it give me the error message 

Could anyone tell me what I'm overlooking here or point me in the right direction?

Try and mount it like this:
> 
sudo mount -t vfat /dev/sda3 /media/IOMEGA_HDD/


---

### Post by Captainm on 2007-04-14
> **freebird54 said:**
> Can't say for sure what is happening there.  It LOOKS like you are trying to mount a partition, not a drive.  If it is a separate device, it won't also be sda# it'll be sdb#...

Could you clarify what you are attempting?
I'm trying to mount a separate usb device. If I change /dev/sda3 to /dev/sdb it gives me > mount: special device /dev/sdb does not exist
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6609    53086761    7  HPFS/NTFS
/dev/sda2            6610        9598    24009142+  83  Linux
/dev/sda3            9599        9729     1052257+   5  Extended
/dev/sda5            9599        9729     1052226   82  Linux swap / Solaris
```

> Try and mount it like this:
```
sudo mount -t vfat /dev/sda3 /media/IOMEGA_HDD/
```

Gives me the same error message as before. I could be wrong but isn't that doing the same thing as I already did?

---

### Post by freebird54 on 2007-04-14
Well - sda3 already exists, and is a ext3 drive - so you can't mount it as a vfat drive.  I don't any aign that the drive you want to mount is even detected by the system.  The fdisk -l should have shown you the device.  Are you sure it is recognized at all?

---

### Post by jordanmthomas on 2007-04-14
Your problem is that sda3 is the extended partition.  You want the extended partition's "meat", which is sda5.
Also, it is a Linux parition, not FAT32
Hope this helps.

**edit** beaten

---

