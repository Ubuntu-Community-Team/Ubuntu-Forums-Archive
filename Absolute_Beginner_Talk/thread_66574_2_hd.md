---
title: "2 hd"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-09-17
I have just put in an extra 20 gig hdd in. I was wondering how i would acces it? I have a 40 gig master drive and now a 20 gig slave drive. I had ubuntu on my 40 gig before i put in the extra 20 gig. I just dont know how to access my 20gig for extra space.

---

### Post by atrus325 on 2005-09-17
You'll have to mount it.  It'll probably show up under hdb (with your master drive being hda).

$ mkdir /path/to/where/i/want/this/drive
$ mount /dev/hdb /path/to/where/i/want...

You'll probably have to be superuser to mount it.

If the drive has multiple partitions, they'll show up as hdb1, hdb2, etc.

If you've already formated/partitioned this drive in Windows, ignore the stuff below.

To partition the drive, you can just use fdisk.  

Make sure.. ABSOLUTE SURE.. you don't fdisk hda rather than hdb.  That would be a bad thing.

Anyway, that's how I'd do it in Gentoo.  It's probably the same in Ubuntu.

J.

Edit.. Oh yeah, and if you haven't done so, you'll need to give the drive a filesystem as well.  $ mke2fs /dev/hdb or $ mkreiserfs /dev/hdb ....  Like I say, all this, with the exception of the stuff on mounting the drive, assumes you haven't done this stuff in Windows already. -- J.

---

