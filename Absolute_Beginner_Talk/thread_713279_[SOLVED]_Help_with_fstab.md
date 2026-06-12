---
title: "[SOLVED] Help with fstab"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by kryth on 2008-03-02
Ubunutu crashed on me now i can't write to external h/d. It's read only. I can't change it with chmod, but no luck. I've tried messing with fstab, but i don't know enough.

here's my fdisk -l and fstab

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              14         673     5295104    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             674        1955    10297665    5  Extended
/dev/sda3   *        1956        8329    51199155    7  HPFS/NTFS
/dev/sda4            8330       19457    89385660   83  Linux
/dev/sda5   *         674        1891     9783553+  83  Linux
/dev/sda6            1892        1955      514048+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13e3bee0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    5  Extended
/dev/sdb5               1       19457   156288289+   b  W95 FAT32



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda5 
UUID=41f02cb6-d821-4226-904f-f1e294e5d929 /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda6  
UUID=a6ef89d0-84b9-4fdc-84b2-6047710277df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0  


I've also tried adding
/dev/sdb6 /media/disk vfat unmask=000 0 0
or something like that but that didn't work.

any clues?
Thanks.

---

### Post by kryth on 2008-03-02
Or is there a way to completely rebuild fstab from scratch?

---

### Post by Crooksey on 2008-03-02
Remove the hardrive from fstab, then when you plug it in HAL should mount it with correct permissions.

---

### Post by kryth on 2008-03-02
> **Crooksey said:**
> Remove the hardrive from fstab, then when you plug it in HAL should mount it with correct permissions.



Didn't work :(

---

### Post by Crooksey on 2008-03-02
Try..

```

/dev/sdb6 /media/disk vfat defaults
```

In fstab, but before reboot...

```

$ sudo chmod -R 777 /media/disk
```

---

### Post by kryth on 2008-03-02
Nope. Just can't get it off read only.

---

### Post by kryth on 2008-03-03
okay I think i fixed it.

---

