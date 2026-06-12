---
title: "KERNEL PANIC!! Please help! Unable to mount root filesystem!"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-11-17
OH NO!

I might have messed something up in Gparted..

When I boot it says:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

Could someone please help me get my linux back.

I have a dual boot vista/ubuntu setup..

---

### Post by Inxsible on 2007-11-17
boot up with a live cd and try ```
sudo fdisk -l
```if you formatted with gparted then you would be out of luck :(

---

### Post by systemintheglitch on 2007-11-17
what does that do, and once i do it what should i do after
?

---

### Post by Skefflock on 2007-11-17
It shows all the partitions that you have on you system. And you have to post the output here, so anybody could help you than.

---

### Post by systemintheglitch on 2007-11-17
/dev/sda1               1         619     4965376   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         619        7854    58114258    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            7855        9645    14379120   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            9645        9729      680400    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            9645        9729      680368+  82  Linux swap / Solaris


So ummm

sda1 and sda2 are really important windows partitions.. One is a restore partition.. Hope nothings wrong.

---

### Post by systemintheglitch on 2007-11-17
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4965376   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         619        7854    58114258    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            7855        9645    14379120   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            9645        9729      680400    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            9645        9729      680368+  82  Linux swap / Solaris


```

Sorry.. Like I said all my partitions are very important.

---

### Post by systemintheglitch on 2007-11-17
By the way this is all gparted's fault. 
I was clicking around in gparted.. Didn't commit any changes, and then gparted failed with a segfault and crashed!  Next time i tried to boot up, it gave that error.

---

### Post by systemintheglitch on 2007-11-17
Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f78f7d77-c408-4c29-8bdb-dd9c45b5a5fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=400E6D160E6D066E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=3050ADD550ADA1D8 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=76fc3585-e08b-49d1-96e6-562b8a51dda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda2    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

---

### Post by systemintheglitch on 2007-11-17
Noone? Please help guys. I'm startin to get worried.

---

