---
title: "[SOLVED] External HDD problem...."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2008-02-12
My external Disk mounts with no problem....but when i try to move some files into it i get a message error:

You do not have permissions to write to this folder.

How to fix this?? How to access an external driver with root permission?

thanks

---

### Post by cool_penguin on 2008-02-12
What does this mean? I...????:lolflag:

---

### Post by nikolas68 on 2008-02-12
> **cool_penguin said:**
> What does this mean? I...????:lolflag:

...ooopps...press the wrong button but edited correctly.

---

### Post by kpkeerthi on 2008-02-12
What is the filesystem type? How are you mounting the device? Can you post the outputs of
1. sudo fdisk -l
2. mount
3. cat /etc/fstab

---

### Post by nikolas68 on 2008-02-12
> **kpkeerthi said:**
> What is the filesystem type? How are you mounting the device? Can you post the outputs of
1. sudo fdisk -l
2. mount
3. cat /etc/fstab
 
[ [IMG]http://www.imagehosting.com/out.php/i1574073_ScreenshotdiskProperties.png[/IMG]](http://www.imagehosting.com)

Thanks for helping. It's a ext2 system. It mounts when i plug it in. The driver is partitioned in 4 and this specific partition i cannot use it. I've tried to reformat in fat 32 but won't work.
AND there's something inside the disk that i don't know what it is...and i've never placed it there!!

---

### Post by nikolas68 on 2008-02-12
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb38a2ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3033    24362541    7  HPFS/NTFS
/dev/sdb2            3034        7421    35241984    b  W95 FAT32
/dev/sdb3            7421        8912    11979776    7  HPFS/NTFS
/dev/sdb4            8912        9730     6564864    f  W95 Ext'd (LBA)
/dev/sdb5            8913        9730     6563840    b  W95 FAT32

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f3db9333-d4a3-bc8e-7ef0-5233059d4ed2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=484E2E504E2E36DA /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2088a70a-46f4-4da8-8b69-c9959fe2f111 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by kpkeerthi on 2008-02-12
> **nikolas68 said:**
> 
Thanks for helping. It's a ext2 system. It mounts when i plug it in. The driver is partitioned in 4 and this specific partition i cannot use it. I've tried to reformat in fat 32 but won't work.
AND there's something inside the disk that i don't know what it is...and i've never placed it there!!

Can you try mounting it manually. 
```

sudo umount /dev/sdb5
sudo mkdir /media/windows
sudo mount /dev/sdb5 /media/windows/ -t vfat -o iocharset=utf8,umask=000

```

**Note:** Change /dev/sdb5 to the relevant partition you are trying to write to.

---

### Post by nikolas68 on 2008-02-12
...really appreciate your help....but it's not working!!

```
nicola@ubuntu:~$ sudo mount /dev/sdc2 /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by kwacka on 2008-02-12
In the image in message 5 we see its an ext2 partition. It won't mount as a vfat partition.

You tell us that you can already mount & read from the partition but not write to it, and you last message suggests its located at /dev/sdc but this doesn't show up in your post showing the output of fdisk -l.

Assuming you can mount the partition.

Click on the "permissions' tab on the original of that image and find who owns the rights to write to that partition and amend it to include your self.

The safe way: in a terminal type:
 sudo chown -R root user /media/disk3  (or wherever it is located)

(assuming 'root' is the owner and replacing 'user' with your user name)

The dangerous way: in a terminal type
sudo nautilus

and right-click on the partion, select properties, and check the boxes to allow permissions - click the box at the bottom to change the properties of enclosed files. IMMEDIATELY close nautilus - you can do a lot of damage running nautilus as root.

---

### Post by nikolas68 on 2008-02-12
> **kwacka said:**
> In the image in message 5 we see its an ext2 partition. It won't mount as a vfat partition.

You tell us that you can already mount & read from the partition but not write to it, and you last message suggests its located at /dev/sdc but this doesn't show up in your post showing the output of fdisk -l.

Assuming you can mount the partition.

Click on the "permissions' tab on the original of that image and find who owns the rights to write to that partition and amend it to include your self.

The safe way: in a terminal type:
 sudo chown -R root user /media/disk3  (or wherever it is located)

(assuming 'root' is the owner and replacing 'user' with your user name)

The dangerous way: in a terminal type
sudo nautilus

and right-click on the partion, select properties, and check the boxes to allow permissions - click the box at the bottom to change the properties of enclosed files. IMMEDIATELY close nautilus - you can do a lot of damage running nautilus as root.

THANKS: i did the safe way and it worked!!!

---

