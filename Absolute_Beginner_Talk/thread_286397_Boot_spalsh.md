---
title: "Boot spalsh"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-10-27
Ok so I was updating to edgy and when I started I noticed that when I started the live CD there was no boot-splash just a blinking cursor. I thought that it might work when I installed it cause it would install all the drivers and everything. I was wrong. There is no boot-splash when I start up just a blinking cursor. It doesn't pose a problem every thing works fine it is just that the start up is so crappy with a black screen with a blinking cursor in the top left corner. Anyone had this problem too? anyone know how to fix it or even if I can fix it?

Thanks.

---

### Post by ReaderRat on 2006-10-27
Do you get the Boot Menu? Does the screen go blank at login, when X starts?

---

### Post by erichnewell on 2006-10-27
Check your /boot/grub/menu.lst for the kernel options you are loading. At the end of the "kernel" line you should see the word "splash". If not, add it.

---

### Post by PPAAUULL on 2006-10-27
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

That is what it says in the file.

---

### Post by petgraveyard on 2006-10-27
> **erichnewell said:**
> Check your /boot/grub/menu.lst for the kernel options you are loading. At the end of the "kernel" line you should see the word "splash". If not, add it.

I am having the same problem, yet it also says splash on the end for me:

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash

Help?

---

### Post by PPAAUULL on 2006-10-27
Yes Help Please!!!

---

