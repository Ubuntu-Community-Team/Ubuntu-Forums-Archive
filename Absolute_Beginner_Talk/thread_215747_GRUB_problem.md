---
title: "GRUB problem"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Tedd on 2006-07-14
Hey,

I just reinstalled Windows XP and rescued my system with the Dapper disk. But GRUB doesn't detect Windows XP, how can I add it to the GRUB menu?

---

### Post by [S|G] on 2006-07-14
add this entry to your /boot/grub/menu.lst:
```

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

You need to know the partition that your windows is installed. This assumes that your windows partition is /dev/hda1. If it is /dev/hdb2, for example, change the line ```
 root            (hd0,0)
``` to ```
 root            (hd1,1) 
```

---

