---
title: "grub sees windows but does not load it"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by ironchief on 2007-01-07
Ok, so I have recently loaded ubuntu 6.10 onto my windows machine. It has one hard drive. Upon completion of the installation i could boot into ubuntu from grub but I am unable to boot into windows. It does show windows as an option though and says starting boot.... but does not go anywhere. This makes my first linux installation a very sad one. But hey, now I have a shotgun wedding to Ubuntu before school starts on Monday! Please help me return to windows.

---

### Post by energiya on 2007-01-07
Please post your /boot/grub/menu.lst file. Maybe something is wrong in there.

---

### Post by pay on 2007-01-07
/boot/grub/grub.conf (or /boot/grub/menu.lst as energiya suggested. I forget which Ubuntu uses) should have something like this ```
title=Windows XP
rootnoverify (hd0,2)
makeactive
chainloader +1
```Where hd0 is the primary harddrive and 2 is the 3rd partition on that drive.

---

### Post by energiya on 2007-01-07
I have
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

for my Windows in /boot/grub/menu.lst

---

### Post by ajmorris on 2007-01-07
i think it should be title=Microsoft.... try it and see what happens.

---

### Post by Bigbluecat on 2007-01-07
If that does not work can you also post the output of:

```
sudo fdisk -l
```

Let's see if it is pointing to the correct partition.

---

### Post by ironchief on 2007-01-07
fdisk shows

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23889   191888361    7  HPFS/NTFS
/dev/hda2           23890       36105    98125020   83  Linux
/dev/hda3           36106       36483     3036285    5  Extended
/dev/hda5           36106       36483     3036253+  82  Linux swap / Solaris

and I am pretty sure that grub shows

title Microsoft Windows XP Media Center
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by ironchief on 2007-01-07
yup it shows

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by mips on 2007-01-07
Try **[GAG]("http://gag.sourceforge.net/")**. Much easier to use, no configs to screw around with, all graphical.

---

### Post by pay on 2007-01-07
> **ironchief said:**
> fdisk shows

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23889   191888361    7  HPFS/NTFS
/dev/hda2           23890       36105    98125020   83  Linux
/dev/hda3           36106       36483     3036285    5  Extended
/dev/hda5           36106       36483     3036253+  82  Linux swap / Solaris

and I am pretty sure that grub shows

title Microsoft Windows XP Media Center
root (hd0,0)
savedefault
makeactive
chainloader +1Well everything appears  correct (to my knowledge). Maybe it's a problem on the Windows side.:confused:

---

### Post by ironchief on 2007-01-07
do I need to put in ```
rootnoverify (hd0,0)
```?

And if so how? hmm, could it be that windows was destroyed by Gparted's resizing of its partition?

---

