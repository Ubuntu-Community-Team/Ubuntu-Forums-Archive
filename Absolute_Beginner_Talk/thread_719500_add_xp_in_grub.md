---
title: "add xp in grub"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2008-03-09
hi i have read some of the previous threads on this topic but i failed to add xp anyway

my fdisk -l output : 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76713521

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8393931   27  Unknown
/dev/sda2   *        1046       19458   147895917+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62b34b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1045        5576    36396484+   7  HPFS/NTFS
/dev/sdb2            5577       14087    68364607+  83  Linux
/dev/sdb3   *       14088       18887    38556000    7  HPFS/NTFS
/dev/sdb4           18888       19457     4578525    5  Extended
/dev/sdb5           18888       19457     4578493+  82  Linux swap / Solaris


my xp is located on /dev/sdb3 .  it tried adding 
#XP
title          Microsoft Windows XP Professional
root           (hd1,2)
savedefault
makeactive
chainloader    +1

with no success . any ideas ?

---

### Post by Duck2006 on 2008-03-09
Add to these lines,

title Microsoft Windows XP Professional
root (hd1,2)
savedefault
makeactive
chainloader +1

To look like this,

title Microsoft Windows XP Professional
root (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

That will let win think it is the first disk in the system (C:\ Drive)

---

### Post by neoragexxx on 2008-03-09
i have tried this and i get error 11 : unrecognised device string

#XP
title             Microsoft Windows XP Professional
root             (hd1,2)
map            (hd0)(hd1)
map            (hd1)(hd0)
savedefault
makeactive
chainloader    +1

---

### Post by Duck2006 on 2008-03-09
Have you tried changing the root line from

root (hd1,2)

To

root (hd1,1)

The windoze is in the second partition of the drive witch grub see as 1 not 2 (counts from 0 not 1)

---

### Post by neoragexxx on 2008-03-09
i tried it right now after you mentioned it but i still get the same error

---

### Post by Duck2006 on 2008-03-09
Device Boot Start End Blocks Id System
/dev/sdb1 1045 5576 36396484+ 7 HPFS/NTFS
/dev/sdb2 5577 14087 68364607+ 83 Linux
/dev/sdb3 * 14088 18887 38556000 7 HPFS/NTFS
/dev/sdb4 18888 19457 4578525 5 Extended
/dev/sdb5 18888 19457 4578493+ 82 Linux swap / Solaris

So your win is on sda3?
If so try

title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by neoragexxx on 2008-03-09
no it's sdb3 !

---

### Post by Duck2006 on 2008-03-09
> **neoragexxx said:**
> no it's sdb3 !

Is the linux drive your boot drive? Ie you changed it in your BOIS

---

### Post by neoragexxx on 2008-03-09
no, should i do that ?

---

### Post by Duck2006 on 2008-03-09
You can try super grub live cd to fix you menu.lst

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

And here is the grub page that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by neoragexxx on 2008-03-09
unbelievable .. i did a fresh installation of ubuntu and it still doesn't find my xp installation :( . the weird part is that the xp installation is just fine cause i can access it if i use anothe boot manager like acronis os selector

p.s: i've already tried super grub with no success

---

