---
title: "Automate bootloader"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by cmac1602 on 2007-10-09
Hi, have read up on grub but I'm still a bit confused.  When my PC boots up, I get 2 kernels and memtest86+. Any idea how I get grub to automatically boot up?

The extract from my menu.lst is as follows:

[COLOR="Blue"]title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-12-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




[/COLOR]

Many thanks

---

### Post by skymera on 2007-10-09
auto boot up?

you mean boot up a selected kernel with out you saying so?

if yes

[www.getdeb.net](www.getdeb.net)

search for 

```
 Startup Manager 
```

good tool

---

### Post by Shazaam on 2007-10-09
Change the timeout value to 0. To get access to the different kernal choices hit Esc during boot.

---

### Post by Bliepo32 on 2007-10-09
Edit: someone else was earlier with his suggestion. Mine is not needed anymore.

---

### Post by cmac1602 on 2007-10-10
Nah, changing the timeout to 0 doesn't have any effect - I've got two kernels set at 'savedefaults'. Is this the problem?

---

### Post by eph1973 on 2007-10-10
You want it so you don't see GRUB, and it pretty much just chooses your default OS?  Try setting timeout to 1 and uncomment the word hiddenmenu (you'll have 1 second to change your mind about the kernel you want, and you'll need to hit escape to see the GRUB menu).  You won't see your GRUB menu, although you will still see the business about loading GRUB stage 1.5 and all that, then it'll just skip right on through to the boot process.  You might like [this]("http://ubuntuforums.org/showthread.php?t=567971") also.

---

### Post by cmac1602 on 2007-10-10
Thanks, will give it a go.

---

