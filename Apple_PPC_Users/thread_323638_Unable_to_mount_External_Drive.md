---
title: "Unable to mount External Drive"
date: 2006-12-22
forum: Apple PPC Users
---

### Post by st4rscream on 2006-12-22
Unable to mount "sda3":

mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount
_____________________________________________________________________________

Anyone know what to do here?
I been all over trying to figure this out.

I am trying to mount an external HD it has 2 partitons both were formatted in OS X with the Unix format option.

---

### Post by shane2peru on 2006-12-22
Open a terminal  **Applications - Accessories - Terminal** (assuming you are using Gnome)  and type:
```

dmesg | tail

```  Then paste the output to that here.  Also the output of ```
sudo fdisk -l
```  And also finally ```
cat /etc/fstab
```  That will help us get started.

Shane

---

### Post by st4rscream on 2006-12-23
@ubuntu:~$ dmesg | tail
[186726.505615]   Vendor: WDC WD40  Model: 0BB-00JHC0        Rev:  0 0
[186726.505687]   Type:   Direct-Access                      ANSI SCSI revision: 00
[186726.516539] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[186726.516564] sda: assuming drive cache: write through
[186726.527559] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[186726.527588] sda: assuming drive cache: write through
[186726.527606]  sda: [mac] sda1 sda2 sda3 sda4
[186726.556998] sd 15:0:0:0: Attached scsi disk sda
[186726.557180] sd 15:0:0:0: Attached scsi generic sg0 type 0
[186726.577745] usb-storage: device scan complete

_________________________________________________

I cant get the 2nd part it goes too fast and then I cant copy it

--------------------------------------------------------
@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by shane2peru on 2006-12-23
Ok, what you need to do is expand the terminal window to make it full screen.  You have a lot of hard drives.  After you make the window full screen you should be able to copy and paste it here:
```

sudo fdisk -l

```

that is an lowercase L in case you were wondering.  Or you can just copy it and paste it into the terminal.  

Shane

---

### Post by st4rscream on 2006-12-28
/dev/sda
        #                    type name                 length   base     ( size )  system
/dev/sda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/sda2               Apple_UFS Plunder            12582912 @ 64       (  6.0G)  Unknown
/dev/sda3               Apple_UFS Loot               65582376 @ 12582976 ( 31.3G)  Unknown
/dev/sda4              Apple_Free                           8 @ 78165352 (  4.0k)  Free space

Block size=512, Number of Blocks=78165360
DeviceType=0x0, DeviceId=0x0

/dev/hdc
        #                    type name                 length   base     ( size )  system
/dev/hdc1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hdc2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hdc3         Apple_UNIX_SVR2 untitled           76246094 @ 2018     ( 36.4G)  Linux native
/dev/hdc4         Apple_UNIX_SVR2 swap                1876888 @ 76248112 (916.4M)  Linux swap

Block size=512, Number of Blocks=78125000
DeviceType=0x5007, DeviceId=0x501f
Drivers-
1: @ 105928633 for 58625, type=0xf3a4
2: @ 3418209799 for 45316, type=0x386e
3: @ 8128885 for 4995, type=0xc510
4: @ 3807694104 for 35829, type=0x83c6
5: @ 273249305 for 14380, type=0x74f6
6: @ 2696218548 for 770, type=0x8000
7: @ 8405384 for 512, type=0x8
8: @ 4202744448 for 59987, type=0x7c00
9: @ 3260558 for 55438, type=0xd0bc
10: @ 2161568 for 16508, type=0x3cff

This last part with the drivers or whatever goes on for a thousand #s

---

### Post by didg on 2006-12-28
Does it mount sda2?

I'm not sure that pmount,hal, whatever understand UFS .

as a test you can try to use mount, read only.

mount -t ufs -o ro /dev/sda3 /mnt/*something*

---

### Post by indica on 2007-09-11
BUMP THIS THREAD

I'm getting theabove EXACT same error.  I swapped my external and internal hdd's to get the larger one into my lappy.  I had to store all my files on a lacie drive connected to a powermac.  I reformatted the now external drive as unix and threw all the files back on, now my linux ibook won't read it, none of the macs or a windows comp at my one job won't read it either.  I'm hoping to put it back on the powermac today and see if i can at least still access the files.  This means the world to me, can anyone give me any ideas?

Pleeeeeease (I'm not below begging, or bribery)

---

### Post by jemmrich on 2007-12-06
I had the same error output as st4rscream, I also tried didg's line but it failed. I know your question is old, but im replying more so i dont forget or if someone else has this problem.

Here is what worked for me to mount a UFS

```
mount -t ufs -o ro,fstype=ufs2 /dev/sda3 /mnt/somewhere
```

It seems -t ufs is not enough so you have to imply it again with the -o param

Hope this helps someone.

James

---

