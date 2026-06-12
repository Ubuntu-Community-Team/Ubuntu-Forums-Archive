---
title: "sda1 failing to mount but not really"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2008-02-03
I am failing to notice the cause of the following:

When I type sudo mount -all

The error message results: Failed to access 'dev/sda1' no such file or directory

and yet I can see the contents of the drive in media/sda1

Under Gparted dev/sda shows as unallocated partition and filesystem. It is a  true rade drive running off a 3ware card.

This is my fstab. 

```
proc /proc proc defaults 0 0
tmpfs /dev/shm tmpfs defaults,ro 0 0
usbfs /proc/bus/usb usbfs auto 0 0
# Entry for /dev/hda1 :
UUID=221d448e-c456-4e67-b1f4-675a654e16c8 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0 0
# Entry for /dev/hda5 :
UUID=5abbef3f-03f4-4927-868f-93ec33fe1a6f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
# /dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb6 /media/hdb6 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd1 /media/f ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd5 /media/win2k4msi ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
```

what is going on?

I am running fiesty

---

### Post by jan quark on 2008-02-03
what does 

```
sudo fdisk -l
```

show?

---

### Post by Robbyx on 2008-02-03
Wonderful to see such a quick reply. Thank you:

> Disk /dev/sda: 250.0 GB, 250058301440 bytes
64 heads, 32 sectors/track, 238474 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13790   110768143+  83  Linux
/dev/hda2           13791       14593     6450097+   f  W95 Ext'd (LBA)
/dev/hda5           13791       14593     6450066   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391    b  W95 FAT32
/dev/hdb2              14         268     2048287+  83  Linux
/dev/hdb3             269        2169    15269782+  83  Linux
/dev/hdb4            2170        5005    22780170    f  W95 Ext'd (LBA)
/dev/hdb5            3700        4591     7164958+   7  HPFS/NTFS
/dev/hdb6            2170        3699    12289662    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2549    20474811    7  HPFS/NTFS
/dev/hdd2            2550        5004    19719787+   f  W95 Ext'd (LBA)
/dev/hdd5            2550        5004    19719756    7  HPFS/NTFS


---

### Post by jan quark on 2008-02-03
try this

```
sudo mount /dev/sda /media/sda -t ntfs -o nls=utf8,umask=000
```

but before you do this what do

```
mount
```

and 

```
ls /media 
```

show

---

### Post by Robbyx on 2008-02-03
I assume that you were advising me to run first mount:

```
/dev/hda1 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
tmpfs on /dev/shm type tmpfs (ro)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw,iocharset=utf8,umask=000)
/dev/hdb5 on /media/hdb5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdb6 on /media/hdb6 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdd5 on /media/win2k4msi type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
/dev/hdb3 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/hdb2 on /media/disk-1 type ext3 (rw,nosuid,nodev)
/dev/hdd1 on /media/f type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

```

then 
ls /media
```
cdrom   cdrom1  disk-1  floppy   g  hdb1  hdb6  J         Olympus_DR  sdb1     vfatdata   windows
cdrom0  disk    f       floppy0  h  hdb5  hdb7  KINGSTON  sda1        usbdisk  win2k4msi

```

Should I now run the mount command you suggest?

---

### Post by jan quark on 2008-02-03
try and tell me what has exploded :)

---

### Post by Robbyx on 2008-02-03
```
ls /media
cdrom   disk    floppy   h     hdb6  KINGSTON    sdb1      win2k4msi
cdrom0  disk-1  floppy0  hdb1  hdb7  Olympus_DR  usbdisk   windows
cdrom1  f       g        hdb5  J     sda1        vfatdata

```

---

### Post by Robbyx on 2008-02-03
```
robin@robin-desktop:~$ sudo mount /dev/sda /media/sda -t ntfs -o nls=utf8,umask=000
Password:
mount: mount point /media/sda does not exist

```

---

### Post by Robbyx on 2008-02-03
In case you meant sda1 I also tried 

```
robin@robin-desktop:~$ sudo mount /dev/sda /media/sda1 -t ntfs -o nls=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Robbyx on 2008-02-04
It was going so well. A great correspondence. Do you have a solution?

---

### Post by jan quark on 2008-02-04
try to create the mount point first

```
sudo mkdir /media/sda or sda1
```

---

### Post by Robbyx on 2008-02-04
The mount point is already there and it contains the rade drive contents known as sda1.

---

### Post by jan quark on 2008-02-04
robbyx sorry but it is midnight in germany and i cannot think properly anymore :)
g2g and get some sleep

but will come back to this thread tomorrow

---

### Post by Robbyx on 2008-02-07
I hope you have some more suggestions.

---

