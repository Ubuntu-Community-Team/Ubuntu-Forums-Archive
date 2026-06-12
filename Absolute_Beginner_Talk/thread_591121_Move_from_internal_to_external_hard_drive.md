---
title: "Move from internal to external hard drive"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by audiofreq on 2007-10-25
Hi,

I got given a usb external hard drive and decided to take the hard drive out and put it in my computer. The other drive in that PC only has XP on it.

So i disconnected the XP hard drive, connected the external one internally (IDE) and installed ubuntu on it. I did it like that because i just wanted to play around with ubuntu for a while (without being restricted by the speed of the live CD).

Anyway, so i decided i like it but want to use that drive externally again.

So i've taken the drive out and put it back in it's USB housing...connected it to my computer...selected boot from usb in the bios and started up with my fingers crossed.

I was pleased to see that GRUB loaded but i was just given the basic grub terminal.

What i was wondering, is if it was possible to change my grub conf file so that it knows where ubuntu is installed? This is just to save me reinstalling with the new set up.

Also, if it is possible and i get that working is it possible to add my XP drive to the GRUB menu too?

Ideally...i want to set my bios boot order to CD - > USB - > HDD then if the usb drive it powered on i will be given the option to boot Ubuntu or XP, and if the USB drive is off...then it will just boot into XP automatically...

I don't want to have to mess with the XP drive really...

Thanks in advance.

---

### Post by audiofreq on 2007-10-25
Here is my menu.lst

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6d492f0e-a7d4-43ce-b787-4398dee104b3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6d492f0e-a7d4-43ce-b787-4398dee104b3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

---

