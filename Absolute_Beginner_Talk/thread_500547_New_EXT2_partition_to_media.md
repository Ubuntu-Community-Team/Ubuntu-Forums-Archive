---
title: "New EXT2 partition to /media"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by JumpyLINUX on 2007-07-14
I split the last partition on my harddisk wich is NTFS and made an EXT2 partition at the end. I did the partitioning in Windows. How can I get the new EXT2 partition to show in /media/ where all the other partitions are listed? Is there a way to re run the "script" that the Kubuntu installation did?


PS: I'm using Kubuntu.

---

### Post by m@ra on 2007-07-14
Humm.. Windows doesn't support making of EXT2 partitions as far as I know. Or yes with some 3rd party tools.


Open terminal

sudo bash                                
#open terminal session as a root

ls /dev
#see listing for hdXX or sdXX (partitions that exists in your system) hd for ATA and sd for SATA

mkdir /media/diskname       
#(create a mountpoint to your disk)

mount /dev/hdXX or SdXX /media/diskname
#mount [device] [destination] ext2 shouldn't require file type definition

---

### Post by Cappy on 2007-07-14
you may need to change the permissions after to get read/write:
```
sudo chown -R $USER:$USER /media/folder_you_made_for_the_mount
sudo chmod -R 755 /media/folder_you_made_for_the_mount

```

---

### Post by JumpyLINUX on 2007-07-14
> **m@ra said:**
> 
mkdir /media/diskname       
#(create a mountpoint to your disk)
mount /dev/hdXX or SdXX /media/diskname
#mount [device] [destination] ext2 shouldn't require file type definition

Will this make the new partition mount automatically on startup like the old ones?

---

### Post by JumpyLINUX on 2007-07-14
**Could the answer lie in /etc/fstab?**
I know the partition I need to add is sda8, but what kind of line do I need to add to the fstab?

Here's what mine looks:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=b5f007d4-8c8b-440d-b632-222e62b70daa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A6E414F2E414C689 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=08B088CDB088C324 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=B4648B17648ADB8C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=666C8E0E6C8DD8E7 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=23b80983-ef92-4ca0-956c-84f56b49acf4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

