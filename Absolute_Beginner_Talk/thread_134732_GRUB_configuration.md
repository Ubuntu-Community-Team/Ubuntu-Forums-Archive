---
title: "GRUB configuration"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by cobweb on 2006-02-22
I have installed a new linux version 2.6.12
I constructed the executable from the source code and copied it to the /boot directory with the name newkernel-2.6.12

the menu.lst file in my /boot/grub directory looks like:
title Ubuntu, kernel 2.6.12-9-386
root (hd0,6)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro single
initrd /boot/initrd.img-2.6.12-9-386
boot

I added these lines in order to add my new kernel,

title Ubuntu, kernel newkernel(2.6.12)
root (hd0,6)
kernel /boot/newkernel-2.6.12 root=/dev/hda7 ro quiet splash
boot

but it suspended while booting it after restarting, what could be the problem, how should I have changed menu.lst?

thanx in advance

---

### Post by Sutekh on 2006-02-23
I'm far from an authority on kernel compilation.  

Don't Ubuntu kernels need an initial ram disc - initrd?

When you created the kernel, using **sudo make-kpkg** (I think this is the command), did you use the **--initrd** flag?

I guess if you did, there should be a line, similar to the other kernels,
```
initrd /boot/initrd.img-2.6.12-9-386
```

Really you should hope for better advice, sorry!

Perhaps you can run us through the commands that you used to compile the kernel source.

---

