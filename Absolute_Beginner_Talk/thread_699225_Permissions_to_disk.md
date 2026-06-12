---
title: "Permissions to disk"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Vinillum on 2008-02-17
I can't create folders/files in my systems's main disk. I couldn't create them even in other folders in my system disk, but I changed permissions to them by "sudo chown -R root:plugdev (folder)" ( I am not even sure if root:plugdev is right. I've just found that kind of permissions in other of my disks which wasn't blocked for new folders ). Now I need to make such permissions to the main page of the system's disk, but I don't know how to call it. I have tried "media:/sda1/" but it doesn't work. Any help?

---

### Post by jan quark on 2008-02-17
pleaes run these commands and post the output

```
mount
```

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by Jimcanoa on 2008-02-17
and
```
groups
```

---

### Post by Vinillum on 2008-02-17
[[[[[[[[[[[[[[[[[[[[[[[ mount ]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,defau
lt_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

[[[[[[[[[[[[[[[[ sudo fdisk -l ]]]]]]]]]]]]]]]]]]]]]]]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd65dd65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        9728    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2551        9728    57657253+   7  HPFS/NTFS
/dev/sda6            2433        2550      947772   82  Linux swap / Solaris

Partition table entries are not in disk order

[[[[[[[[[[[[[[[[[[[[ cat /etc/fstab ]]]]]]]]]]]]]]]]]]]]]]]]]]]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=94c60027-83ca-4422-895d-d1806a53c152 /               ext3    defaults,error                                                                                                   s=remount-ro 0       1
# /dev/sda5
UUID=121896E91896CB5D /media/sda5     ntfs    defaults,umask=007,gid=46 0                                                                                                          1
# /dev/sda6
UUID=dfedf1bf-e033-4936-a474-36adbe7a39ed none            swap    sw                                                                                                                 0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

[[[[[[[[[[[[[[[[[[ groups ]]]]]]]]]]]]]]]]]]]]]]]

vinillum adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin                                                                                                    netdev powerdev

---

### Post by jan quark on 2008-02-17
try this

```
sudo chmod -R 755 /dev/sda1
```

---

### Post by Vinillum on 2008-02-17
Still the same...

---

### Post by jan quark on 2008-02-17
```
 chown -R username:username /dev/sda1
```

change username to your username for instance bob:bob

---

### Post by Vinillum on 2008-02-17
Nope... Still nothing...

---

### Post by Vinillum on 2008-02-19
Well, the problem is still unsolved, but I've come up to a better idea... I know use "Krusader" in root-mode, which allows me to do anything in my disk... Thanks for help, anyway.

---

