---
title: "Grub Problems"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Brooze on 2006-10-09
menu.lst

First Try:
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

Boot: Absolutely nothing happens.

Second Try:
title Windows XP
map (hd1) (hd0)
map (hd0) (hd1)
rootnoverify (hd0,0)
makeactive
chainloader +1

Boot:  Gives me - Invalid or unsupported executable format

any ideas?

---

### Post by Kateikyoushi on 2006-10-09
How are your partitions set up ?

```
sudo fdisk -l
```


This is from my grub.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Brooze on 2006-10-09
Running the fdisk gives me:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5113    41070141   83  Linux
/dev/hda2            9332        9729     3196935    5  Extended
/dev/hda3            5114        9331    33881085   83  Linux
/dev/hda5            9332        9729     3196903+  82  Linux swap / Solaris
```
a1 - 64B 6.10 Ubuntu Edgy Eft
a2 - ?
a3 - 32B 6.06 Ubuntu Dapper Drake
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4997    40138371    7  HPFS/NTFS
```
Which is the Windows XP drive.

Linux didn't automatically put in an entry for my Windows drive because I installed the two completely seperately.  ie - I unplugged the Windows drive and installed linux to a brand new disk and then I am trying to plug the Windows disk back in as a slave drive now.

---

