---
title: "I/O problem with USB drive"
date: 2007-03-22
forum: Apple PPC Users
---

### Post by epee1221 on 2007-03-22
I'm trying to mount a USB HD (currently formatted as hfs). When I try to mount it, it complains.
```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

`dmesg | tail` gives this:
```
[ 1041.542164]  sda:<6>sd 0:0:0:0: SCSI error: return code = 0x10070000
[ 1041.887150] end_request: I/O error, dev sda, sector 0
[ 1041.968389] sd 0:0:0:0: SCSI error: return code = 0x10070000
[ 1041.968404] end_request: I/O error, dev sda, sector 0
[ 1041.968412] printk: 2 messages suppressed.
[ 1041.968420] Buffer I/O error on device sda, logical block 0
[ 1041.969358]  unable to read partition table
[ 1154.100011] sd 0:0:0:0: SCSI error: return code = 0x10070000
[ 1154.100026] end_request: I/O error, dev sda, sector 2
[ 1154.100539] hfs: can't find a HFS filesystem on dev sda.

```

I tried to reformat it using both fdisk and mac-fdisk. It says 
```
fdisk: Can't write block 0 to file  (Input/output error)
fdisk: Can't write block 1 to file  (Input/output error)
fdisk: Can't write block 2 to file  (Input/output error)
The partition map has been saved successfully!
```

Looking back at it shows that the partition table was not saved.

---

### Post by epee1221 on 2007-03-25
bump

---

### Post by pxwpxw on 2007-03-26
What is the usb drive type and size and how and with what macos format was it formatted (i,e, by macos on a mac or what).  

Did you try 
```

sudo mount -t hfsplus /dev/xxx yyy

```
If you want to format hfs from ubunt try hfsutils , hformat (man hfsutils).
fdisk and mac-fdisk are partitioners noit formatters,
Also man mkfs.

---

