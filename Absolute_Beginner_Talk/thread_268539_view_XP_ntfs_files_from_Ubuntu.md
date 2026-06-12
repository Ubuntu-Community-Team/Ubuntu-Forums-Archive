---
title: "view XP ntfs files from Ubuntu"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by stmcc on 2006-09-30
I have a dual boot XP and Ubuntu. I am unable to mount an access to the XP files. I have tried a half dozen approaches , but nothing works. My XP files are on hda1 and hda5. Ubutu is on hdb
MAC

---

### Post by hyper_ch on 2006-09-30
```

sudo mkdir /media/hda1
sudo mkdir /media/hda5

```

then edit /etc/fstab
```

sudo nano /etc/fstab

```

and add at the end
```

/dev/hda1 /media/hda1 ntfs ro,defaults,umask=0222 0 0
/dev/hda5 /media/hda5 ntfs ro,defaults,umask=0222 0 0

```

That will give you read access to the ntfs drives.
You can replace /media/hdaX with whatever you want.

---

### Post by jaboua on 2006-09-30
Can you please post the output of "sudo fdisk -l /dev/hda"? I suspect that you might have tried to mount an extended partition instead of the real partition.

---

### Post by haxer on 2006-09-30
Can i do the same with an linux partiton to get i shown if thats the case how to do?

---

### Post by stmcc on 2006-09-30
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1946    15631213+   7  HPFS/NTFS
/dev/hda2            1947        4865    23446867+   f  W95 Ext'd (LBA)
/dev/hda5            1947        4865    23446836    7  HPFS/NTFS

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         442     3550333+   7  HPFS/NTFS
/dev/hdb2   *         443         765     2594497+  83  Linux
/dev/hdb3             766         784      152617+   5  Extended
/dev/hdb5             766         784      152586   82  Linux swap / Solaris
stmcc@stmcc-desktop:~$
](*,)

---

### Post by haxer on 2006-09-30
Try this sudo mount -a

---

### Post by stmcc on 2006-09-30
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/hda1 ntfs ro,defaults,umask=0222 0 0

/dev/hda5 /media/hda5 ntfs ro,defaults,usask=0222 0 0
still unable to read XP files:confused:

---

### Post by devils_casper on 2006-09-30
> /dev/hda1 /media/hda1 ntfs ro,defaults,**umask=0222** 0 0

/dev/hda5 /media/hda5 ntfs ro,defaults,**usask=0222** 0 0

umask should be 0 and correct the spellings in second line.

/dev/hda1 /media/hda1 ntfs ro,defaults,umask=0 0 0
/dev/hda5 /media/hda5 ntfs ro,defaults,umask=0 0 0



casper

---

### Post by stmcc on 2006-09-30
Thanks!!!!!!
every one. I can now read my XP files with Unbutu from boot(/) Is there a way that I can move that to the HOME dir???
MAC :KS

---

### Post by devils_casper on 2006-09-30
what do you mean by move.. ?

you can create a sym link of NTFS drive on Desktop.

ln -sf /media/hda /home/*user_name*/Desktop/Windows_c




casper

---

### Post by stmcc on 2006-09-30
Problem solved.  Icons for my XP SYSTEM and DATA {hda1 & 5 } showed up on my Desktop. They were underneath other Icons. When I sent the ones on top to the trash, They poped up. This will work fine. Thanks very much for all your help. MAC:D

---

### Post by devils_casper on 2006-09-30
:D you are welcome stmcc !!




casper

---

