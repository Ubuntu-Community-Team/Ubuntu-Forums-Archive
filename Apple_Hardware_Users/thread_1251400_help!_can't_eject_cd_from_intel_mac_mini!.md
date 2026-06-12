---
title: "help! can't eject cd from intel mac mini!"
date: 2009-08-27
forum: Apple Hardware Users
---

### Post by user sam on 2009-08-27
I recently came up with a hare brained scheme to install both bsd and ubuntu linux on the same mac mini. after ubuntu installed the grub, my computer began to boot from the cd drive automatically. After I installed freebsd 7.2,  I couldn't remove the installation media. I tried holding down left click on startup, but the disk is still there and I can't do anything outside of the very limited bsd shell on the cd. does anyone know how I might force the disk to eject without entirely dismantling my computer? :evil:

---

### Post by gwydionwaters on 2009-09-24
from within linux, type ```
eject cdrom
``` into the terminal

---

