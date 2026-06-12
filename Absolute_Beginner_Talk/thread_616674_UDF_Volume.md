---
title: "UDF Volume"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-18
Ubuntu 7.10 will not read my CD.
See result of dmesg

bernard@bernard-desktop:~$  dmesg | tail
[ 1193.503832] UDF-fs: No fileset found
[ 1193.652856] Unable to identify CD-ROM format.
[ 1243.483545] UDF-fs: No VRS found
[ 1243.526184] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1243.559921] ISOFS: changing to secondary root
[ 1906.313876] UDF-fs: No fileset found
[ 1906.473641] Unable to identify CD-ROM format.
[ 2119.723080] UDF-fs: No fileset found
[ 2119.883892] Unable to identify CD-ROM format.
[ 2159.711651] UDF-fs: No fileset found

The fstab line is:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Is there anything I can do to get the CD to open. No problem with the iso9660 file system.
Thanks

Bern

---

### Post by Arwen on 2007-11-18
Same [thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=510748") about mounting a DVD-R Udf.Check your fstab line carefully.

---

### Post by philinux on 2007-11-18
Are you running gutsy or feisty?

I'm on gutsy

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

but in feisty it was /dev/hdc and hdd

---

### Post by bern1939 on 2007-11-18
I am afraid no success with any option taken from the post you mention.

bernard@bernard-desktop:~$ sudo mount -t udf /dev/scd0 /media/cdrom0/

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I wonder what can I do?

Bern

---

### Post by Fibonacci on 2008-02-07
Same here. Manually mounting doesn't work either.

---

