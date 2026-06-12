---
title: "Non-default console resolution does not work in gutsy"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-11-03
I prefer using a higher resolution for the console as it makes Linux feel alot more modern and less dos-like.

In feisty I added vga=794 to the boot entry in GRUB and it worked, but I havent been able to get it working in Gutsy.

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ceafa094-5575-42d3-8245-1b8548925bee ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

I just get a black screen when I go into a console, when I remove the vga=794 it works, but its a low resolution.

---

### Post by jw5801 on 2007-11-03
It's a known [bug](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) with the current kernel. If you have a scroll through the comments on that bug report there's a fix. It involves adding a couple of modules to the initramfs. Look about two thirds down. If you can't get it working post back here and I'll give you a hand. I'm not at my Ubuntu machine at the moment so I can't give you more detailed information right now.

---

