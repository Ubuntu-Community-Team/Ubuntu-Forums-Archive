---
title: "Windows gone in menu.lst, please help"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by MatsB on 2006-02-17
Hi

After I run the latest updates for Ubuntu my dual boot option for Windows seem to be gone in the menu.lst file and the file menu.lst~is an exact copy :cry: 

Could someone please help me to restore what or what I should put in the menu.lst to get my Windows back.


Thanks,
Mats

---

### Post by aysiu on 2006-02-17
If your Windows partition is at the beginning or your first hard drive, this may help: ```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by MatsB on 2006-02-17
[QUOTE=aysiu]If your Windows partition is at the beginning or your first hard drive, this may help: ```
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```[/QUOTE]

So this should work for my first physical hardrive right? I have Ubuntu on my second physical harddrive. I should also mention that it is SATA disks if that matters.

Thanks

---

