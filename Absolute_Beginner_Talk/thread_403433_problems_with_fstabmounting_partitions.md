---
title: "problems with fstab/mounting partitions"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by dragonschild on 2007-04-07
ok, i have on windows XP in fat32 format a partition 128 megs named drive G, i see it in gparted, but cant seem to access it so i was fooling around with fstab ( made a backup first) and tried to add it to it under /media so i could access it and saved and now i cant even access the windows partition ( i double click/right open and nothing happens) How do i restore my backup, and how do i make it so i can access this partition so i can watch my amv/s anime while on Ubuntu?


                   

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=3532a9c9-2e5c-4fdb-ac04-9b09fa8714f3 /               ext3    defaults,erro$
# /dev/hda1
UUID=22B81B6DB81B3EAB /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hda3
UUID=b8b3e6da-9f52-492f-931e-ee571799116e none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda4 /media vfat defaults 0 0







                               [ Read 12 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


thats what my fstab looksl ike atm, did i do somehtign wrong?

---

### Post by confused57 on 2007-04-07
You can restore your backup by:
```
sudo nano /etc/fstab_backup /etc/fstab
```
substitute the name you gave your backup for the first file above.

To access your FAT32 partition from Ubuntu:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

