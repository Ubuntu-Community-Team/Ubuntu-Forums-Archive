---
title: "goes crazy"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by mordeith on 2006-09-09
ok i will try to explain this....i have tried to get comfortable with linux....whe i try to open any thing it seems to stick and then opens the same thing till the computer kinda locks up.....im using the logitech mx1000 mouse w thje standard drives....the only way i can get it to stop is by mashing the esc key...alot....any clues as to why....this happens....its very annoying

---

### Post by nickpaton on 2006-09-09
Hi Mordeith and Welcome to the Forums!

It sounds like your distro is very sluggish in operation.

To speed it up you need to add 'noapic' into Grub as follows:

In a Terminal (Applications>Accessories>Terminal), copy and paste this into it, press enter and ignore any warning messages which come up in the Terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Scroll down to a line which look similar to this:

> title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

At the end of the 'kernel' line add:

> noapic

If you are using Ubuntu on a laptop, also add:

> nolapic

Click on 'Save' and 'Quit'.

(Also close Terminal)

If you are still having problems, please could you send us details of your PC specifications including the CPU, memory, graphics etc.

Good lucK!

---

