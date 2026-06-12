---
title: "Mount Partition"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-04-19
Hi, all.......
Just clean installed Fiesty, and need to mount my other partitions , like
/dev/sdb3            2551        7112    36644265   83  Linux
and my other windows partitions
sdb1 is Fiesty  :)

---

### Post by taurus on 2007-04-19
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb3   /media/sdb3   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb3
sudo mount -a
df -h
```

---

### Post by Drakkor on 2007-04-19
Thanks, taurus, but I get an error ! :( 
godzilla@drakkor-desktop:~$ sudo mkdir /media/sdb3
Password:
godzilla@drakkor-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2007-04-19
Are you sure /dev/sdb3 is ext3?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Drakkor on 2007-04-19
Forgot to add dual booting
sda is drive 1, sdb is drive 2
godzilla@drakkor-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1431    11494476    7  HPFS/NTFS
/dev/sda2            1432        9732    66677782+   f  W95 Ext'd (LBA)
/dev/sda5            1432        4718    26402796    7  HPFS/NTFS
/dev/sda6            4719        5239     4184901    7  HPFS/NTFS
/dev/sda7            5240        9732    36089991    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+  83  Linux
/dev/sdb2            7113        7299     1502077+   5  Extended
/dev/sdb3            2551        7112    36644265   83  Linux
/dev/sdb5            7113        7299     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order
godzilla@drakkor-desktop:~$

---

### Post by taurus on 2007-04-19
Can you post your /etc/fstab as well?

How about if you run this command from a terminal?

```
sudo mount -t ext3 /dev/sdb3 /media/sdb3
```

---

### Post by Drakkor on 2007-04-19
Woohoo !!  :)  thanks taurus,  that command worked !!  Getting all my Fiesty configured,lol got tvtime,streamtuner,xmms, firefox noscript already,lol  :KS

---

### Post by taurus on 2007-04-19
8-)

---

### Post by Drakkor on 2007-04-20
yeah problem again, now the partition didn't show up again
did sudo mount -t ext3 /dev/sdb3 /media/sdb3    and it mounted again !
how can i make it mount permanently ??? thanks :)

---

### Post by Drakkor on 2007-04-20
*bump* :)
Here's the fstab
 
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5fd7dfef-05c9-415b-87c3-61a0062702b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=1fe5a20e-72bf-4514-aca9-cc053187c8c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb3       /media/sdb3     ext3                    0       1

---

### Post by taurus on 2007-04-20
Can you post your /etc/fstab here?

```
cat /etc/fstab
```

---

### Post by Drakkor on 2007-04-20
Just did above, taurus :)

---

### Post by taurus on 2007-04-20
> **Drakkor said:**
> *bump* :)
Here's the fstab
 
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5fd7dfef-05c9-415b-87c3-61a0062702b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=1fe5a20e-72bf-4514-aca9-cc053187c8c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**[COLOR="Red"]/dev/sdb3       /media/sdb3     ext3                    0       1[/COLOR]**

You've missed a defaults variable.

```
/dev/sdb3   /media/sdb3   ext3   **defaults**   0   1
```

---

### Post by Drakkor on 2007-04-20
Yeah, kinda fiqured that out just now, I went with the same as sdb1 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5fd7dfef-05c9-415b-87c3-61a0062702b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=1fe5a20e-72bf-4514-aca9-cc053187c8c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[COLOR="Red"]/dev/sdb3       /media/sdb3     ext3    defaults,errors=remount-ro                0       1[/COLOR]

Does the ro make it read only ?  Thanks taurus :)

---

### Post by taurus on 2007-04-20
Are you planning to write to /media/sdb3?  Personally, I wouldn't include "errors=remount-ro" for /dev/sdb3.  That option should only be used for /.  Therefore, this should be sufficient.

```
/dev/sdb3   /media/sdb3   ext3   defaults   0   1
```

---

### Post by Drakkor on 2007-04-20
Ok, thanks, taurus :)  I rebooted and it's fine now......mounted and everthing !  :)

---

