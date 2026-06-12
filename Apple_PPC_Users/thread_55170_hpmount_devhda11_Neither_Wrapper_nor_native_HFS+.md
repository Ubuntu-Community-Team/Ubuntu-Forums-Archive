---
title: "hpmount: /dev/hda11: Neither Wrapper nor native HFS+"
date: 2005-08-07
forum: Apple PPC Users
---

### Post by trash on 2005-08-07
It seems my hfs+ partition has problems:(
I no longer osX or cd's to repair and os9 won't mount the partition.
Are there any LINUX tools to repair an hfs+ partition.

errors:
sudo mount /dev/hda11
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda11,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

kenji@bigmac:~$ sudo hpmount /dev/hda11
*** Warning: You are about to open '/dev/hda11' for writing ***
*** Do you really want to do that ? (y/n) ***
y
hpmount: /dev/hda11: Neither Wrapper nor native HFS+ volume header found (Unknown error 4294967295)

---

### Post by jasmuz on 2005-08-08
hfsutils - Tools for reading and writing Macintosh volumes
Did you try checking the system with one of the tools contained in this package?

---

### Post by trash on 2005-08-08
nope, it says its for HFS but nothing about HFS+

---

