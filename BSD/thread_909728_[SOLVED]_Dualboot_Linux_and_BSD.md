---
title: "[SOLVED] Dualboot Linux and BSD"
date: 2008-09-03
forum: BSD
---

### Post by liquidfunk on 2008-09-03
If I were to do so, can I install BSD after Linux, or would it be better the other way round?

---

### Post by Sorivenul on 2008-09-03
As one who has done it, I suggest BSD and then Linux.  This mainly has to do with GRUB vs say the FreeBSD bootmenu.  If you Linux install doesn't recognize your BSD install, a simple entry like this will work in your GRUB menu:
```

title FreeBSD
root (hd0,0,a)
kernel /boot/loader
```

This, of course, assumes FreeBSD, which I would suggest for BSD beginners, as I believe it is easier to set-up and configure than the other two major players.  

Good luck!

EDIT:
Of course you can install BSD after Linux, but I would suggest not installing the bootmenu and just editing the Linux GRUB menu as above.

---

### Post by liquidfunk on 2008-09-03
Thanks for your help, do Nvidia cards work ok in BSD, same as Compiz?

---

### Post by cardinals_fan on 2008-09-03
> **liquidfunk said:**
> Thanks for your help, do Nvidia cards work ok in BSD, same as Compiz?
On FreeBSD (and its spawn, DesktopBSD and PC-BSD).  NVIDIA hasn't released drivers for Net, Open, or DragonFlyBSD.

---

### Post by Sorivenul on 2008-09-03
I don't know about nVidia drivers for FreeBSD, as I run Intel chipsets on pretty much all my machines.  As for Compiz, it runs fine:
```

cd /usr/ports/x11-wm/compiz-fusion/
make install clean
```

And wait.  :)  

Or:
```
pkg_add -r compiz-fusion
```

---

### Post by liquidfunk on 2008-09-03
Thanks a lot for your help guys!

---

