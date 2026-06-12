---
title: "lilo or grub with ur fries sir?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Anoobiz on 2006-11-13
ive just installed ubuntu in addition 2 my mandrake 10.2 and windows partition. windows is added 2 grub but not mandrake. how do add mandrake 2 the grub booloader. plz help... i cant loose my mandrake :(. thx... Anoobiz

---

### Post by an.echte.trilingue on 2006-11-13
You need to add a section to /boot/grub/menu.lst that points to your mandrake install.

A section looks like this (you probably have many):

```
title           Debian GNU/Linux, kernel 2.6.17-2-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-2-686 root=/dev/hda1 ro quiet vga=792
initrd          /boot/initrd.img-2.6.17-2-686
savedefault
```

You can title it any way you want.  Under kernel, you need to add the location of your kernel and the hard drive it is on (root=).  Under initrd, you need to point it to the right initrd image, which almost always has the same version number as the kernel.

That's it.

Good Luck!

-mat

---

### Post by Anoobiz on 2006-11-13
Thanx mat i was just able 2 grasp that. i followed ur advice with a little help tho. u see i have 2 identical setups on 2 pc'z and i was able 2 copy the locations of the kernel and initdr files as they do reside in the same directories and hda.. thx mat.. Anoobiz :)

---

### Post by an.echte.trilingue on 2006-11-13
Glad to be of help.

---

