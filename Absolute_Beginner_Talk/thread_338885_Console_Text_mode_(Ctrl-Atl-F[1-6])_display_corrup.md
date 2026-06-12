---
title: "Console Text mode (Ctrl-Atl-F[1-6]) display corrupted and unusable?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by stormyuk on 2007-01-15
Hello,

Its day 3 of Linux/Kubuntu for me and after talking to my friend he suggested using CTRL-ALT-F[1-6] to jump into the console window either at boot if I have problems or from x-windows to read logs etc.

The trouble is if I try and use any other screen than F7 I get a complete full screen of corruption, lots of pretty colours all over the screen like about 20 tins of paint have been thrown over it, it might qualify for art but its not usable as a console! :)

I am using Kubuntu Edgy 6.10 with ATI fglrx (X1900) + xorg.

Any ideas?

Thanks,

Mike

---

### Post by Koybe on 2007-01-15
- Try switching a few screens.
- Try to login without seeing anything and then use the 'clear' command.

Maybe this could help.

---

### Post by Zaffe on 2007-01-15
Try add "vga=0x318" in the kernel load in /boot/grub/menu.lst
Example:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash vga=0x318
```[/QUOTE]

---

### Post by stormyuk on 2007-01-15
> **Zaffe said:**
> Try add "vga=0x318" in the kernel load in /boot/grub/menu.lst
Example:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash vga=0x318
```

Thanks for the help both of you, that worked a treat Zaffe! I love these forums.

Thanks again,

Mike :)

---

