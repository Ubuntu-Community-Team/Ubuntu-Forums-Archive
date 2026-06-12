---
title: "mount problems"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-02-19
wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ferby@ferby-desktop:~$ sudo umount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umas=0222
umount: invalid option -- o
Usage: umount [-hV]
       umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-f] [-r] [-n] [-v] special | node...
ferby@ferby-desktop:~$ dmesg | tail
[17202030.428000] sd 1:0:0:0: Attached scsi removable disk sda
[17202030.428000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17202030.436000] usb-storage: device scan complete
[17202033.892000] UDF-fs: No VRS found
[17202033.908000] UDF-fs: No VRS found
[17202034.092000] Unable to identify CD-ROM format.
[17202034.284000] Unable to identify CD-ROM format.
[17202034.296000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17203958.436000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17203958.436000] NTFS-fs error (device hdb1): parse_options(): Unrecognized mount option umas.


It windows xp slave  hard drive was working fine,  now I can not access to it anymore, and it gives me that information.
Since I installed kubuntu I did not have the need to mount manually , it was there already, or maybe I did it manually but only one time, It was working fine

Any Ideas?

---

### Post by kelbizzle on 2007-02-19
If your looking to mount your slaved hard drive thats located at /dev/hdb1 and mount it at /media/windows type into terminal:
```
sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
that will mount it manually.

If you want to unmount the drive
```
sudo umount /media/windows
```

If you want to mount it on boot...type. You have to edit your fstab. 
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

```
 Add this line..
```
/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0

```
then remount the fstab manually with this command
```
sudo mount -a
```

You should have read only access to your files on that partition located at /media/windows

---

### Post by gigaferz on 2007-02-21
thank you , Ive never had to deal with this stuff before..

Ill give it  a try,

---

