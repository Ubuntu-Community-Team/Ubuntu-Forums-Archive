---
title: "vista and ubuntu dual boot on a single HD"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mahehellraiser on 2007-12-07
I read all the posts on dual boot of vista...now mine is a new problem......
i had vista pre-installed and then i installed ubuntu i have both ubuntu and vista in the grub
when i try to boot vista ...system restarts ..no matter how many times i tried,  the same result...

---

### Post by mahehellraiser on 2007-12-07
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15356928    7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        4462    20482843+   7  HPFS/NTFS
/dev/sda6            4463        7012    20482843+   7  HPFS/NTFS
/dev/sda7            7013        8924    15358108+   7  HPFS/NTFS
/dev/sda8            8925        8986      497983+  82  Linux swap / Solaris
/dev/sda9            8987        9729     5968116   83  Linux

---

### Post by mahehellraiser on 2007-12-07
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title  Microsoft Windows Vista 
root   (hd0,0)  #Remember Vistas partition number
savedefault
makeactive
chainloader +1

---

### Post by mahehellraiser on 2007-12-07
and i tried all combinations of numbers ..for (hd0,x)....(x)........:(

---

### Post by mahehellraiser on 2007-12-10
can anyone sort this out...

---

