---
title: "Ubuntu &amp; win xp"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by leonsmit2003 on 2005-06-20
Hi, Guys
Need some help with dual booting. I have 2 seperate hard drives. Master have a Ubuntu installation (ext3 FS) and on the other as a slave drive winxp installation (NTFS Fs). How do I get Ubuntu to start so that I have a choice of which o/s to boot into? 
Any help would be appreciated

---

### Post by blind0wl on 2005-06-20
Grub didnt pick it up automatically?

Follow this if you need to add WinXP to your grub conf file
[http://www.ubuntuguide.org/#addwindowsentrygrubmenu](http://www.ubuntuguide.org/#addwindowsentrygrubmenu)

If your windows disk is seen as hdb replace the:
```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

with:

```
title		Microsoft Windows
**root		(hd1,0)**
savedefault
makeactive
chainloader	+1

```

---

### Post by leonsmit2003 on 2005-06-21
no, I installed Ubuntu as a single drive then slaved my win xp drive. Ubuntu is my boot drive

---

### Post by blind0wl on 2005-06-21
Yeh...if you follow the guide you should be right....

---

