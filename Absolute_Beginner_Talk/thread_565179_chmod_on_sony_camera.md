---
title: "chmod on sony camera"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]Hi. I've got a sony dsc-p1 digital camera. I can move files from it but I can't delete or write files to it.
I'm the owner already. tried chmod and it just keeps telling me its a read only file system
> ramses@backroom:/media/disk-1$ chmod a+rwx -R DCIM
chmod: changing permissions of `DCIM': Read-only file system
chmod: changing permissions of `DCIM/100MSDCF': Read-only file system
chmod: changing permissions of `DCIM/100MSDCF/DSC00049.JPG': Read-only file system
Obviously I'm doing something basic wrong.
Ideas?
[/FONT]

---

### Post by bodhi.zazen on 2007-10-02
I assume the file system is either FAT or NTFS.

Neither file system supports ownership and permissions are set at the time of mounting (so chmod/chown will not work).

Can you post the output of :

sudo fdisk -l

(with the device attached)

Or tell us the file system ?

---

### Post by carloslosgrande on 2007-10-02
[FONT="Comic Sans MS"]file system is vfat[/FONT]
ramses@backroom:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1401    11253501   83  Linux
/dev/sda2            1402       19452   144994657+   5  Extended
/dev/sda5           19069       19452     3084480   82  Linux swap / Solaris
/dev/sda6            3946       19068   121475466   83  Linux
/dev/sda7            1402        3945    20434617   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641   83  Linux

Disk /dev/sdc: 32 MB, 32473088 bytes
4 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         990       31670+   1  FAT12
ramses@backroom:~$

---

### Post by bodhi.zazen on 2007-10-02
Well, you can either install ntfs-config

```
sudo apt-get install ntfs-config
sudo ntfs-config
```

* You will have to enable your repos first
*ntfs-config works with both vfat and ntfs

Or manually re-mount

```
sudo umount /media/foo
sudo mount -t vfat /dev/sdxy /media/foo -o uid=1000,gid=100,umask=000
```

Change /media/foo to your mount point and /dev/sdxy to the actual device

---

