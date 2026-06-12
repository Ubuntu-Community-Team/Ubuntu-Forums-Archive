---
title: "can not read dvd file"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by fsshl on 2005-09-21
I had unbuntu linux 2.6.8 kernel
  and hitachi dvd camcorder, I shoot some still photo using it record on small dvd disk, when I put the small disk to my toshiba dvd rom, and issue

mount -t udf /dev/cdrom /cdrom
It response
mount: medium not found

  Is that possible it is too small to be detected?  It can be read by my hp laptop's dvd drive.

  looking for advancer's help
fsshl

---

### Post by mlomker on 2005-09-23
> mount -t udf /dev/cdrom /cdrom


Are you sure that is the proper device name for your CD-ROM drive?  Mine is /dev/hdc.

You can check by searching your kernel log:

```

dmesg | grep CD

```

---

### Post by fsshl on 2005-09-25
it response nothing
----------------------------------
 # dmesg | grep CD
root@etutor:/home/fsshl # dmesg | grep CD
root@etutor:/home/fsshl # dmesg | grep CD
root@etutor:/home/fsshl # dmesg | grep CD
root@etutor:/home/fsshl #

----------------------------------
(I tried both cdrw which write regular window file
and
dvd ram which record (either or both dvd-moving-film or still camera photo shot) from my Hitachi's dvd camcorder
)
 
my cdrw have 24X 700mb  80 min, the data can be rechecked by my xp computer's dvd cdrw combo

my dvd ram disk is smaller than usual size of regular cd, but it still can be read to show both moving film and still photo on my xp computer's dvd cdrw combo

my ubuntu linux comouter's toshiba dvdrom drive always no problem to read ubuntulinux 4.10 cd1(iso image), so I guess it is not malfuntion(at least for regular cdR)

looking for more advice

---

### Post by fsshl on 2005-09-28
root@etutor:/home/fsshl# ls /media
cdrom  cdrom0  floppy  floppy0
root@etutor:/home/fsshl# ls /media/cdrom
root@etutor:/home/fsshl# ls /media/cdrom0
root@etutor:/home/fsshl# mount -t udf /dev/dvd /media/cdrom
mount: block device /dev/dvd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/dvd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


# dmesg | tail
[4297464.151000] end_request: I/O error, dev hdc, sector 2379400
[4297476.348000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4297476.348000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4297476.348000] ide: failed opcode was: unknown
[4297476.348000] end_request: I/O error, dev hdc, sector 1248
[4297488.544000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4297488.544000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4297488.544000] ide: failed opcode was: unknown
[4297488.544000] end_request: I/O error, dev hdc, sector 1024
[4297488.545000] UDF-fs: No partition found (1)
root@etutor:/home/fsshl#

-----------------------------------------------------------------------------------------------------------------------------
thsi is what I tried, after I put in the dvdram (smaller than regular dvd disk) after record some still photo shoot from Hitchi dvd camcorder.

please help

---

### Post by mlomker on 2005-09-28
> some still photo shoot from Hitchi dvd camcorder.


I've never tried mounting one of those discs, so I don't know what kind of filesystem it uses.  Do regular DVD's work?

Try **mount /dev/hdc /media/cdrom0**

---

### Post by fsshl on 2005-09-29
[QUOTE=mlomker]I've never tried mounting one of those discs, so I don't know what kind of filesystem it uses.  Do regular DVD's work?

Try **mount /dev/hdc /media/cdrom0**[/QUOTE]
-------------------------------------------------------------------------------------------------------------------
If you mail me a DVD(movie or data file) I am glad to (test)
ebay address: 903 7th st s, Great Falls, MT 59405  (tester)

---

