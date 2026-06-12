---
title: "Kernel Panic error"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-11-01
i was tryin to make my laptop look like OSX Leopard to prove to a friend that i could... anywho i used [this guide](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

ive tried over and over to get the boot screen to change and on my last try when i restarted i got this beautiful error

```
Starting up....
[     7.207702] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

anyone know wut that could mean? also if i acces GRUB i can get the laptop to boot on kernel 2.6.20-16 but the one im having issues with is 2.6.22-14 any ideas how to fix this?

---

### Post by killaray on 2007-11-01
no one?

---

### Post by markharding557 on 2007-11-01
try restoring a backup of your menu.1st file
open as root in an editor /boot/grub/menu.1st~ and then rename it menu.1st
note no squiggle
you may see menu.1st.backup you could try also

---

### Post by killaray on 2007-11-01
ive checked both one that boots and the back up and both seem to be exactly the same... there was one line that wasnt and i removed it, though the issue continued

---

### Post by hafees on 2007-11-03
Hi,

Me too have the same problem. I tried restoring the menu.1st. but no use. 

Please help.

Thanks

---

