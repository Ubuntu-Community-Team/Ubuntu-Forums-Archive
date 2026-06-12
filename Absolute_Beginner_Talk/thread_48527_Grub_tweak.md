---
title: "Grub tweak?"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by | MM | on 2005-07-12
I want to increase the count down, that grub has before it resorts to loading Ubuntu, is this easily done.

---

### Post by Xian on 2005-07-12
Open the /boot/grub/menu.lst and find the line that begins, 'timeout'.
Set the number to the amount of delay seconds you would prefer.
```
$ sudo gedit /boot/grub/menu.lst
```

---

### Post by | MM | on 2005-07-13
[QUOTE=Xian]Open the /boot/grub/menu.lst and find the line that begins, 'timeout'.
Set the number to the amount of delay seconds you would prefer.
```
$ sudo gedit /boot/grub/menu.lst
```[/QUOTE]

Thank you :D

---

### Post by byen on 2005-07-13
[QUOTE= Xian ]$ sudo gedit /boot/grub/menu.lst[/QUOTE]
 Or you could use "grubconf" a grub configuration utility with a lot more options. I think its available on synaptic.

---

### Post by | MM | on 2005-07-13
Instead of restarting, is there a way to drop out of Ubuntu straight to grub?

So i can boot Windows straight away?

---

### Post by Xian on 2005-07-13
[QUOTE=| MM |]Instead of restarting, is there a way to drop out of Ubuntu straight to grub?

So i can boot Windows straight away?[/QUOTE]
No, you need to let the system shutdown properly.

---

