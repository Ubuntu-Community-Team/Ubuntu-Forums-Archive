---
title: "Installed XP and no -more grub..."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-02-04
Hey guys, i installed XP and dont know how to get grub back, it seemed to overwright the boot, does anyone know of a way of fixing it? (using live cd?)

Thanks in advance.

---

### Post by highneko on 2007-02-04
I always use this guide:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
When you're done you would then have to add windows to your /boot/grub/menu.lst file.

---

### Post by shareMenaPeace on 2007-02-04
Checkout
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

or search the forum for "grub" + "reinstall" like
[http://ubuntuforums.org/search.php?searchid=13985617](http://ubuntuforums.org/search.php?searchid=13985617)

---

### Post by jml on 2007-02-04
You will probably find this out in the supplied links, but if you anticipate doing a dual boot, always install Windows first.  It always overwrites the Master Boot Record (MBR.)  Preventing you from booting into any other OS.  If you can successfully repair the MBR great, if not, you may have to reinstall Ubuntu.

Joe

---

