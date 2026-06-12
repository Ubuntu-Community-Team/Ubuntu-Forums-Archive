---
title: "pioneer dvd r/rw does not work for dvd, only for cd"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by fulviooliveira on 2007-06-30
hi

my ide pioneer dvd r/rw does not mount or record dvd. i'm only trying to read/write data dvds.

it works fine for reading/recording cd-roms, 

some information:
$ dvd+rw-mediainfo /dev/hdb
INQUIRY:                [PIONEER ][DVD-RW  DVR-104 ][1.20]

$ sudo mount /dev/dvd dvd
mount: block device /dev/dvd is write-protected, mounting read-only
mount: you must specify the filesystem type

$ sudo mount -t udf /dev/hdb dvd
mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
(specifying other filesystems produce the same result)

$ dmesg | tail
[19862.252000] hdb: tray open
[19862.256000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[19862.256000] end_request: I/O error, dev hdb, sector 0
[19862.256000] EXT3-fs: unable to read superblock
[19935.904000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[19935.984000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[19936.036000] hdb: tray open
[19936.040000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[19936.040000] end_request: I/O error, dev hdb, sector 64
[19936.044000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16

$ sudo hdparm /dev/hdb
/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

fstab:
/dev/dvd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Spyro-50 on 2007-12-30
I've got a Pioneer drive and it's not working too.

I used K3B and I found that k3b could have access to DVD's name but still, I coundn't mount it with DVD's. Then I tried a CD in this DVD drive and I could see in K3B the files that where in that CD.

Anyone knows why do this happen? Thks in advance

---

### Post by doorknob60 on 2007-12-30
Try changing where it says udf in the fstab to auto, it helped me with similar problems.

EDIT: i guess I'm just talking to spyro as this thread is 6 months old...

---

