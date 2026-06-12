---
title: "FS Check Problem. Answer needed soon"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by regomodo on 2007-11-17
Umm. If it is not too much to ask, i wouldn't want to be of too much bother, but if i'm running 

$reiserfsck -rebuild-tree 

on an ext3 partition should i STOP NOW or just see what happens.

I don't believe this. At least i made a backup, of sorts, a week ago.

i've got 55mins until it completes

---

### Post by regomodo on 2007-11-17
51 minutes.

Anyone? Help. It's like Speed 2

---

### Post by regomodo on 2007-11-17
21minutes

come on guys. it seems this is always the case

---

### Post by regomodo on 2007-11-17
well, the result of mount -av is

> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



I don't like it when my threads look like i'm talking to myself. Is anyone with some idea of how to sort this issue. Should i run fsck on it?

I need a slap

[edit]
fsck /dev/sdb1 gave:

> 

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


---

### Post by Herman on 2007-11-18
First check that your file system really is an ext3 file system.

If it really has a missing or bad superblock, that's easy to fix normally, [What to do if you have a bad ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup"), unless of course they've all been damaged.

Regards, Herman :)

---

