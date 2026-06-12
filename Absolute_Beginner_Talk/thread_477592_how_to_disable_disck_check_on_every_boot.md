---
title: "how to disable disck check on every boot?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by laura_glow on 2007-06-18
Hi, i just installed feisty fawn, and every time i boot, it does a complete file check for all my hard drives. how do i disable it? which file to edit?

thanks!

---

### Post by laura_glow on 2007-06-18
sorry, just found the answer: correct me if i'm wrong:

```
fstab options

/etc/fstab is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to mount and where on the file system tree.

A typical fatab entry may look like this:
file.pngCode:

/dev/hda1 / ext3 defaults 1 1 /dev/hdb1 /home ext3 defaults 1 2


The 6th column is a fsck options.

    * 0 = Do not check.
    * 1 = First file system (partition) to check;
          o / (root partition) should be set to 1. 
    * 2 = ALL OTHER file systems to be checked. 
```

thanks

---

### Post by doncristobal on 2007-07-05
I was also annoyed by the never ending fsck at boot, so i found this thread and changed my fstab so that my linux/windows shared data partition (fat32) and the read-only windows (ntfs) partition are _not checked_ (i set their last column in fstab from 1 to 0). 

The computer now boots 2 or 3 times faster :-) :-) :-)

BUT

:?: my question: Isn't this risky? Do i understand the system well, assuming that those partitions are never checked at all? i think if they got checked from time to time, this would not hurt anybody. 
In *man fstab* i did not find the answer. 

Who can help? Thank you very much! :)



P.S. Here my fstab: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=aec1932e-1d0a-447a-863c-ca3a55c20911 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5284826F8482557F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda2
#UUID=1B33-0A00  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=6AE3-F6DF  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=639d8b5a-b514-41a8-bc66-8a58f4f56e54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

