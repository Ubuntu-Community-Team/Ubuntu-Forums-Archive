---
title: "Which hard drive did I install ubuntu on? Help!"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by matheuu on 2007-02-12
Ok, I want to re format an existing drive so it will be a secondary ubuntu drive,
Have no idea what I am doing.... dont really want to start with a fresh install, just loaded heaps of programs up.... have been reading up on it, but not very confident.
if anyone could give me a step by step method (hold my hand)....that would be great!

I guess that hdb1 ,2 and 5 is my ubuntu.... and hda1 is my ex-windows drive(which I think is the master??)...how did it get like this?

Cheers
Mat

[COLOR="RoyalBlue"]oem@mat:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14216   114189988+  83  Linux
/dev/hdb2           14217       14593     3028252+   5  Extended
/dev/hdb5           14217       14593     3028221   82  Linux swap / Solaris[/COLOR]

---

### Post by finer recliner on 2007-02-12
hdb1,hdb2, and hdb5, are all being used for linux partitions.
hda1 is for windows (NTFS)

---

### Post by xpod on 2007-02-12
This might help:) 

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by matheuu on 2007-02-12
Thanks Mate

Im really wanting to get rid of that MS windows rubbish off that poor harddrive, and make it worth while keeping.

---

