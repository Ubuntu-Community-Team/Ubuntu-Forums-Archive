---
title: "weird partition tables"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rygar on 2007-05-06
I had a problem with my partition tables a while back which I managed to fix.

I've been running my system fine now with no residual effects, except that my partition table looks kinda funky in gparted.  Namely, my linux swap partition looks like it's paired with an NTFS partition of mine.  Altogeher, I've got a 40gb Vista partition, a 30gb XP partition, and a 25gb linux partition (plus 1gb swap).

Is there any reason why this should be an issue, and if so, how can I fix it?

In GParted, it shows:

/dev/sda1 ntfs /media/XP
/dev/sda2 extended
-->  /dev/sda5 ntfs /media/Vista
-->  /dev/sda6 linux-swap
/dev/sda3 ext3 /

(why do i have an extended partition?  i dont need one.  why is there no sda4?)

fdisk -l shows:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9063    42082267+   f  W95 Ext'd (LBA)
/dev/sda3            9064       12161    24884685   83  Linux
/dev/sda5            3825        8923    40957686    7  HPFS/NTFS
/dev/sda6            8924        9063     1124518+  82  Linux swap / Solaris

```

like i said, it's certainly not an urgent issue, my computer runs fine.  but that's a funky-looking partition table...

---

### Post by mikewhatever on 2007-05-06
The set up you have is just fine. sda5 and sda6 are logical partitions, as opposed to sda1 and sda3 which are primary. [http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

The extended partition (sda2) contains the two logical ones. In no way are they paired, whatever you mean by that.

---

