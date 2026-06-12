---
title: "whats the diff between kernels?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-09-13
what's the difference of "Ubuntu, kernel 2.6.15-23-386" from "Ubuntu, kernel 2.6.15-26-386"?

i assume that the 26-286 is newer than 23-386... but i don't exactly know the difference of the 2...

is it safe if i comment out the "Ubuntu, kernel 2.6.15-23-386" from menu.lst? cause it irritates me if there are too many options in grub... i'll make it like this...

```
#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot
```

thanks for the help!

---

### Post by Klaidas on 2006-09-13
You had a kernel update and a new kernel has been downloaded. It was automatically added to GRUB.

If your new kernel (26) works well, you can remove the old one (25).

---

### Post by mokmoki on 2006-09-13
oh, ok... by saying remove, does it mean delete from the system, or remove it from the bootloader's list?

---

### Post by Metacarpal on 2006-09-13
Hi mokmoki,

You can comment it out in your menu.lst, or uninstall it entirely, as you like.  A lot of people keep an older kernel or two on their system, as a back-up.  That kernel update has been around a while, though, so removing the older kernel wouldn't be a problem.

---

### Post by mokmoki on 2006-09-13
oh, ok, thanks for the help...

btw, how do you remove a kernel?

---

### Post by christhemonkey on 2006-09-13
This will remove that kernel:
```
sudo apt-get remove linux-image-2.6.15-23-386 
```

---

