---
title: "Drives not get mounted automatically"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-08-15
While booting Ubuntu is giving a message *something* like this:
> "Mounting Local File systems:
Mount:........................doesn't exist
Mount:........................doesn't exist"
The two volumes have to be mounted  manually to access them.

NB:Those two drives were previously *NTFS* formatted.I just reformatted them to ext3 using *Gparted Live CD*.

The file **/etc/fstab** contains:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F4741FCE741F928A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=8240-F37E  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=68E9-02F3  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=d7637bbe-157f-4fc3-b8fd-3931160a45a1 /media/hdb7     ext3    defaults        0       2
# /dev/hdb6
UUID=3a5095da-41f3-4e4e-a768-0c24bf333572 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Awaiting an early reply.....thanks in advance...

---

### Post by Rocket2DMn on 2007-08-15
If the partitions were hda1 and hda5, you need to edit the fstab file to say that they are ext3, not ntfs.
```
gksudo gedit /etc/fstab
```
and change the lines:
```
# /dev/hda1
UUID=F4741FCE741F928A /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
to something like:
```
# /dev/hda1
UUID=F4741FCE741F928A /media/hda1 ext3 defaults 0 1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5 ext3 defaults 0 1
```

More info here:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- very detailed and useful

---

