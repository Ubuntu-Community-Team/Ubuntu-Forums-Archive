---
title: "mounting local filesystem error"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-17
I have "mounting local file system...failed" during startup. 
I have 2 NTFS partitions on my local hd, and also 2 NTFS on a USB hd.  Even I have this as "failed" I can still access my NTFS partitions after GNOME is up.  However, I need to go to terminal and do a "sudo mount -a" to bring up the USB NTFS partitions.

The following is my /etc/fstab file
```

proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222      0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222      0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/sda5       /media/sda5     ntfs    nls=utf8,umask=0222      0       0
/dev/sda6       /media/sda6     ntfs    nls=utf8,umask=0222      0       0
/dev/hda3       /usr            ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Is there anything wrong with the code?

Thanks in advance.

---

### Post by cilynx on 2006-04-17
Check if your USB subsystem is up and running before the local filesystems are mounted in the init scripts.

---

### Post by Dutch on 2006-05-21
I have also a fail with mounting local file system:

paulaccount@PaulIBM:~$ fdisk -l
paulaccount@PaulIBM:~$ sudo fdisk -l
Password:

Schijf /dev/hda: 80.0 GB, 80032038912 bytes
255 koppen, 63 sectoren/spoor, 9730 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            9412        9730     2562367+  1c  Verborgen W95 FAT32 (LBA)
/dev/hda3            1825        3648    14651280   83  Linux
/dev/hda4            3649        9411    46291297+   5  Uitgebreid
/dev/hda5            3649        9241    44925741   83  Linux
/dev/hda6            9242        9411     1365493+  82  Linux swap / Solaris

Partitietabel ingangen zijn niet in schijfvolgorde
paulaccount@PaulIBM:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/hda1/windows ntfs nls=utf8,umask=0222 0 0
/media/ipod  /mnt/ipod vfat user,noauto,umask=000 0 0
paulaccount@PaulIBM:~$

---

