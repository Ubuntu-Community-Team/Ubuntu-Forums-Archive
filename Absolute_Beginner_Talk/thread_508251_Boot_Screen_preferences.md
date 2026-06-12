---
title: "Boot Screen preferences"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-07-24
Hey everyone!

I need a command to disable the boot screen in Kubuntu Feisty. You know, the blue "Kubuntu" with the progress bar on black background that displays before the login screen. It used to be like this in really old versions of Ubuntu, I think possibly back when I was using Ubuntu Hoary? Any way, I just want to be able to see what the computer is doing as it's booting instead of the useless boot screen, if anyone can tell me how to do that, it'd be great!

Thanks!

---

### Post by MrFSL on 2007-07-24
edit /boot/grub/menu.lst

You will have something similar to this:

```
title           
Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=34ad7468-b34c-496a-8fcc-7d1905700f16 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

simply remove "quiet" and "splash"

Easy  huh?

---

### Post by bbzbryce on 2007-07-24
> **AngryMallard said:**
> Hey everyone!

I need a command to disable the boot screen in Kubuntu Feisty. You know, the blue "Kubuntu" with the progress bar on black background that displays before the login screen. It used to be like this in really old versions of Ubuntu, I think possibly back when I was using Ubuntu Hoary? Any way, I just want to be able to see what the computer is doing as it's booting instead of the useless boot screen, if anyone can tell me how to do that, it'd be great!

Thanks!

In /boot/grub/menu.lst remove the instances of "splash" under the kernel lines.

You'll have to manually do this for newly installed kernels though.

---

### Post by AngryMallard on 2007-07-24
OK! It worked. Thanks!

P.S. What part of this file would change the font?

---

### Post by MrFSL on 2007-07-24
This won't actually change the fonts but it will the resolution...

edit /boot/grub/menu.lst

You will have something similar to this:

```

title           
Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=34ad7468-b34c-496a-8fcc-7d1905700f16 ro 
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

simply add vga=792 after ro on line kernel

---

