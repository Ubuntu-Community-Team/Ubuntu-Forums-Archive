---
title: "gparted + maxtor external hd + ext3"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-04-20
this is a brand new out of the box maxtor hd i got for backing things up from both my ubuntu only computers.

i got gparted, have the hd plugged in but unmounted, and told gparted to format it to ext3 instead of ntfs. how do i know its working or done?

dumb qotd: how do u know this is working?

---

### Post by jtraub on 2007-04-20
sudo fdisk -l

---

### Post by lunaz on 2007-04-20
```

sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
gail@badassness:~$
```

edit omg. i should not post on friday nights after a long *** 2 weeks of work. :D i found the button to make it work..... its called apply. :D
/embarrased

---

### Post by jtraub on 2007-04-20
It wasn't formated to ext3.

You can try to use mkfs.ext3 from console
(But read man mkfs.ext3 before)

---

