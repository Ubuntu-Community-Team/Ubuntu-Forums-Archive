---
title: "Access or recover files from Apple hdd with bad S.M.A.R.T. and 05-reallocating sector"
date: 2014-05-26
forum: Apple Hardware Users
---

### Post by Dioscuro86 on 2014-05-26
I have a Macintosh HD (hfsPlus) ```
[/dev/sdc2 on /media/ubuntu/Macintosh HD type hfsplus(ro,nosuid,nodev,uhelper=udisks2)]
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted. 

Disk /dev/sdc: 750.2 GB, 750156374016 bytes 255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device    Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1465149167   732574583+  ee  GPT Partition 1 does not start on physical sector boundary.

``` Diagnostic software tells me that the S.M.A.R.T. status is bad and also that the 05-reallocating sector count is bad.

  I'm trying to recover some data from it without having to spend $600  to ship it to a company that does the manual recover. I don't care about  the disk, it's still under warranty.  I tried to go to mac doctor but  they couldn't get anything out (I think they just tried mounted it on a  mac and runitf MacDrive.)

  I've tried with Windows 7 and I managed to mount the drive but some  software was not seeing it and the only one who did it was too slow and  kind of *crappy*. I'm trying now with Ubuntu in a bootable flashdrive but I cannot open  the media because of input/output errors while reading the .journal file.
Mounting the drive with the system gives this windows message:```
 

 Error mounting /dev/sdc2 at /media/ubuntu/Macintosh HD:
 Command-line mount  -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc2"  "/media/ubuntu/Macintosh HD"' exited with non-zero exit status 32: 
 mount: wrong fs type, bad option, bad superblock on /dev/sdc2,missing  codepage or helper program,
 or other error.In some cases useful info is  found in syslog - try dmesg | tail  or so`


```

I`m addressing this issue with different methods, too long to be listed all, but I`m trying every pieace of information I`m finding so far. I'd love it if someone could point me in the right direction; I have  some fundamental knowledge on computers but I'm not a developer, and recently got into ubuntu just as one alternative.

---

### Post by tgalati4 on 2014-05-26
I'm not sure if hfsplus support is available in the Live USB.  You might have to download and install support during a Live Session.  Just don't reboot.

To see if you have hfs support:

```
apropos hfs
```

If not, then:

```
apt-cache search hfs
```

.
.
.
hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
hfsprogs - mkfs and fsck for HFS and HFS+ file systems

```
sudo apt-get install hfsplus hfsutils hfsprogs
```


Install those and try to mount again.  It's possible that your disk is beyond repair.  When you run out of reallocation space, bad things happen.

If you can mount it, then grab as many files as you can.  If you can't see the directory structure, then try *testdisk* to recreate it.  If that fails, then use *photorec* to perform a mass file-by-file recovery with useless names and no directories.

Don't reboot and don't write to the bad disk.  Many folks suggest cloning the disk first and working with the clone, but you may not have enough time to make a clone before the disk completely fails.

---

