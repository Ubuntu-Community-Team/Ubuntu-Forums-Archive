---
title: "[SOLVED] Unrecognized/unmounted CD/DVDs"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by maaronB on 2007-11-29
The problem I am having is that the DVD-RW doesn't mount when I insert a CD.
If I insert a CD before starting the computer or while it is booting then it recognizes it and works fine, but if I insert it while the system is running then absolutely nothing happens.

 If I go to Places->Computer, right click the cd icon, then hit mount volume I get a pop up saying 
```
**UNABLE TO MOUNT MEDIA**
There is probably no media in the drive.
```


I have also tried doing it from the command line:
```
$ sudo mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I don't know if it is relevant but this is what the /etc/fstab looks like
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```



I want to make the problem clear.  I am not having problems with codecs or playing the DVDs.  They play fine if I put the CD in the computer while it is booting.  But it doesn't even acknowledge them if I put it in after the computer is running.

I don't think it is a hardware problem.  Everything worked fine in 7.04,Mint, and PClinux.  The problem only began when I installed 7.10.  I have also tried several different types of DVDs and CDs.

Of course, any help at all would be greatly appreciated.

---

### Post by maaronB on 2007-11-29
This is the result of dmesg | tail

```

[12653.061845] attempt to access beyond end of device
[12653.061850] sr0: rw=0, want=1575892, limit=751472
[12653.062682] attempt to access beyond end of device
[12653.062687] sr0: rw=0, want=1577132, limit=751472
[12653.063515] attempt to access beyond end of device
[12653.063520] sr0: rw=0, want=1576108, limit=751472
[12653.064347] attempt to access beyond end of device
[12653.064352] sr0: rw=0, want=1575884, limit=751472
[12653.065235] UDF-fs: No partition found (1)
[12653.068518] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

---

### Post by maaronB on 2007-11-29
I don't know if anybody cares but I solved this problem by changing /etc/fstab to this
> /dev/scd0       /media/cdrom0   auto    user,noauto,exec 0       0
 then restarted.  For some reason everything works now.

---

