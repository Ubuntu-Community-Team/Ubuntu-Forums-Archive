---
title: "Problems booting windows xp from grub"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by LJarvis on 2007-05-20
Ok so first i wiped my 120 Hard drive and installed Ubuntu 7.04  on about 70 gigs of it. Then i installed windows xp (SP2) on on the last 40 gigs of it. Windows wiped Grub and my computer started booting straight into windows xp. I reinstalled grub using the live cd for ubuntu the usual way. Now all that shows up in my grub menu is Ubuntu, the kernel, and the memory test for ubuntu. How can i get windows xp to dual boot with Ubuntu?

---

### Post by oilchangeguy on 2007-05-20
> **LJarvis said:**
> Ok so first i wiped my 120 Hard drive and installed Ubuntu 7.04  on about 70 gigs of it. Then i installed windows xp (SP2) on on the last 40 gigs of it. Windows wiped Grub and my computer started booting straight into windows xp. I reinstalled grub using the live cd for ubuntu the usual way. Now all that shows up in my grub menu is Ubuntu, the kernel, and the memory test for ubuntu. How can i get windows xp to dual boot with Ubuntu?

your best bet is to install windows first, then ubuntu.

---

### Post by LJarvis on 2007-05-20
> **oilchangeguy said:**
> your best bet is to install windows first, then ubuntu.

I tried that before and i got the same problem. Is there a problem with my grub loader? should i be using the grub 2.0 loader instead of the 1.5 loader?

---

### Post by confused57 on 2007-05-20
You can try adding an entry to boot Windows, something like this:
```
title              Windows XP
rootnoverify       (hd0,2)
savedefault
makeactive
chainloader        +1
```

To edit your menu.lst, open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo menu.lst
```

then add an entry similar to the one I've listed at the very end of the file, except use your Window's root partition.

---

