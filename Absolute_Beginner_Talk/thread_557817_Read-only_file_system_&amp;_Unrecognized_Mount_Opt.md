---
title: "Read-only file system &amp; Unrecognized Mount Option"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ihrengott on 2007-09-23
So I've got a nice sized HD with 4 partitions, sda1,  & 5-7 Ext3

I've recently been trying to figure out why my filesystem is Read-Only and attempted to edit /etc/fstab to no avail

I tried to add umask=000 to the options replacing "default" or "rw" but now I have a load problem because I guess "umask" isn't correct.

Now in bash I'm trying to edit the file but the system is read only and I cannot remount because fstab isn't correct.

I'm afraid I might have to attempt to reinstall but also haven't found any useful information about that topic.

This seems like a very n00b problem but I would appreciate any help!!!

Thanks for your time,

Sincerely,
Matt

---

### Post by Ozeuss on 2007-09-23
Please post fstab and sudo fdisk -l, that might give people more information so they can help you.

---

### Post by ihrengott on 2007-09-24
Hope this helps anyone interested in helping, please reply if clarification is needed

_fstab_

/dev/sda5
UUID= ... /     ext3    umask=000, errors=remount-ro   0   2

/dev/sda7
UUID= .../2    ext3    defaults   0   2

/dev/sda6
UUID= ...  none    swap   sw   0   0

/dev/scd1
/dev/scd0

_sudo fdisk-l_

/dev/sda1    1         19457      58 GB     5      Extended

/dev/sda5    2436   19457      48 GB     83    Linux

/dev/sda6    1217   2434        1 GB       82    Linux swap / ...

/dev/sda7    1         1215        9 GB       83    Linux

---

### Post by alienexplorers on 2007-09-24
Am I wrong or does linux have to be on a primary partition and not an extended partition to work correctly.  Never saw it done that way!!!

---

### Post by Adramelech on 2007-09-24
boot in live cd, and mount the partition manually to rw, then edit the fstab.

---

