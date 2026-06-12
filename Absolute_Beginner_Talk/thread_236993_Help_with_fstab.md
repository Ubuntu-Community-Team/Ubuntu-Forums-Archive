---
title: "Help with fstab"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-08-15
Ok i edited my fstab a couple of days ago and i mounted on eof windows partitions it was a fat32 partition .. today i opened the fstab and it was empty ..totally empty ..
I type to access the fstab ..sudo nano /etc/fstab...
any help ??

---

### Post by Drakkor on 2006-08-15
Did you save your input after mounting the partitions ? I beleive you have to hit Crl+X,then type Y to save,then Enter to exit out .

---

### Post by D_frag on 2006-08-15
I can't remember but after i exited the terminal that day i opened the fstab again and everything was ok .. whats wierd is that i now even the fstab it doesnt even have the linux partitions that are mounted already (the ones made while installing the Ubuntu) it's totally empty ..blank.. on teh contrary the first time i trioed editing in the fstab it showed me the already configured ...so i was expecting at least to see the other old partition in it .. and i forgot to say the partition i mounted has disappeared from the computer (GUI)

---

### Post by givré on 2006-08-15
try 
```
ls /etc | grep fstab
```
to be sure that you don't have a backup fstab file (when you edit via gedit/kate they create a fstab~)

---

### Post by D_frag on 2006-08-15
ok i managed to open the fstab using the gedit command not the nano ..dunno why maybe anyone can explain  but whats weird is i fint the partition mounted ok but the partiton is not visible at the gui at all .. is that because i mounted it at a directory that i made different from the directory that ubuntu sets i mounted on  /mnt/hd  not /media/windows !!

---

### Post by givré on 2006-08-15
only device mounted on /media are shown on the desktop & on place.
But there are still mounted, you'll just have to browse /mnt/ to show them

---

### Post by xpod on 2006-08-15
Should`nt matter what directory it`s in.../mnt is fine.
As long as you have the correct path in your fstab you should see it.

As long as it`s mounted that is.....Gets confusing dont it....Still trying to figure it all out meself im afraid.

EDIT:Sorry...forgot about that little detail.

---

### Post by Frank Golden on 2006-08-15
> **xpod said:**
> Should`nt matter what directory it`s in.../mnt is fine.
As long as you have the correct path in your fstab you should see it.

As long as it`s mounted that is.....Gets confusing dont it....Still trying to figure it all out meself im afraid.

EDIT:Sorry...forgot about that little detail.
BTW, a totally blank fstab and you would not be able to boot.

---

### Post by D_frag on 2006-08-15
ok now i try mounting via the fstab 
here is what my fstab looks like 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda8       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda7      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda10       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb2      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb8       /media/windows         vfat     rw,auto,nouser,sync  0       0
/dev/hda1      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hda9      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hdb6      /media/windows         vfat     rw,auto,nouser,sync   0       0


and this the error i get when i try 
mount -a



mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


my fdisk-l



   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2063    16571016    c  W95 FAT32 (LBA)
/dev/hda2            2064        9729    61577145    f  W95 Ext'd (LBA)
/dev/hda5            2064        2258     1566306   83  Linux
/dev/hda6            2259        2297      313236   82  Linux swap / Solaris
/dev/hda7            2298        2431     1076323+  83  Linux
/dev/hda8            2432        4862    19526976    b  W95 FAT32
/dev/hda9            4863        7293    19526976    b  W95 FAT32
/dev/hda10           7294        9729    19567138+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hdb5               2        1132     9084757+   b  W95 FAT32
/dev/hdb6            2552        5101    20482843+   b  W95 FAT32
/dev/hdb7            5102        7651    20482843+   b  W95 FAT32
/dev/hdb8            7652        9729    16691503+   b  W95 FAT32
/dev/hdb9   *        1133        2489    10900071   83  Linux
/dev/hdb10           2490        2551      497983+  82  Linux swap / Solaris


ok i fixed some things now while waiting for a reply and apparently the mount stops because it says 

mount: according to mtab, /dev/hda8 is already mounted on /media/windows

mount failed

i even tried  removing hda8 from the fstab but still i get the same error .. should i reboot ??

---

### Post by givré on 2006-08-15
> **D_frag said:**
> 
/dev/hda8       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda7      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda10       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb2      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb8       /media/windows         vfat     rw,auto,nouser,sync  0       0
/dev/hda1      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hda9      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hdb6      /media/windows         vfat     rw,auto,nouser,sync   0       0

You can't mount all your windows partition on the same directory (/media/windows), you will have to create a directory for each partition.

---

### Post by Frank Golden on 2006-08-15
> **D_frag said:**
> ok now i try mounting via the fstab 
here is what my fstab looks like 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda8       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda7      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hda10       /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb2      /media/windows         vfat     rw,auto,nouser,sync   0       0
/dev/hdb8       /media/windows         vfat     rw,auto,nouser,sync  0       0
/dev/hda1      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hda9      /media/windows         vfat    rw,auto,nouser,sync   0       0
/dev/hdb6      /media/windows         vfat     rw,auto,nouser,sync   0       0


and this the error i get when i try 
mount -a



mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


my fdisk-l



   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2063    16571016    c  W95 FAT32 (LBA)
/dev/hda2            2064        9729    61577145    f  W95 Ext'd (LBA)
/dev/hda5            2064        2258     1566306   83  Linux
/dev/hda6            2259        2297      313236   82  Linux swap / Solaris
/dev/hda7            2298        2431     1076323+  83  Linux
/dev/hda8            2432        4862    19526976    b  W95 FAT32
/dev/hda9            4863        7293    19526976    b  W95 FAT32
/dev/hda10           7294        9729    19567138+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hdb5               2        1132     9084757+   b  W95 FAT32
/dev/hdb6            2552        5101    20482843+   b  W95 FAT32
/dev/hdb7            5102        7651    20482843+   b  W95 FAT32
/dev/hdb8            7652        9729    16691503+   b  W95 FAT32
/dev/hdb9   *        1133        2489    10900071   83  Linux
/dev/hdb10           2490        2551      497983+  82  Linux swap / Solaris


ok i fixed some things now while waiting for a reply and apparently the mount stops because it says 

mount: according to mtab, /dev/hda8 is already mounted on /media/windows

mount failed

i even tried  removing hda8 from the fstab but still i get the same error .. should i reboot ?? fdisk -l shows your /dev/hda7 as a linux partition (ext3) while your fstab shows it as vfat.

---

### Post by Drakkor on 2006-08-15
I'm not saying I'm an expert just learning about linux like everyone here,but you might want to check out my hda6 , which is a fat32 partition here:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       vfat iocharset=utf8,umask=000      0       0

And copy that to yours,except your's being hda7 . Good  Luck !  :p

---

### Post by Frank Golden on 2006-08-15
> **Drakkor said:**
> I'm not saying I'm an expert just learning about linux like everyone here,but you might want to check out my hda6 , which is a fat32 partition here:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       vfat iocharset=utf8,umask=000      0       0

And copy that to yours,except your's being hda7 . Good  Luck !  :p
That's how mine is for a Fat32 partition, with partition numbers and mount points
adjusted for my setup. It mounts my Fat32 partition at bootup 
with full permissions. My NTFS lines are the same with partition numbers and mount points adjusted accordingly. Of course my NTFS
partitions are read only, exactly as I want 'em. Those are my XP
partitions, if I can't write to 'em in Ubuntu, I can't screw 'em up.

---

