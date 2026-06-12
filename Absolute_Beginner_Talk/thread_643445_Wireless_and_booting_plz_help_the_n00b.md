---
title: "Wireless and booting plz help the n00b"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by DarkRookie on 2007-12-17
2 question for yall

1. Every time I reboot my machine I must reconnect to my wireless network manully. It is get annoying to do it. Any tips on to make it reconnect on startup

2. After much forums searching I finally got my system to boot up into 7.04. Every time I boot though I have to edit a line of code to make sure it boots. It work any other way. Is there any way to edit the boot process to make it always boot to an edited line.
Some details. I need to get rid of quiet splash and add vga=791 to the second option. I need a way to edit this line and boot using that information.

I hope that makes since to someone out there

---

### Post by Pumalite on 2007-12-17
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Make the changes in the kernel line
Save, exit, reboot.

---

### Post by DarkRookie on 2007-12-17
ok just need a little detail. sorry

```
1 title		Ubuntu, kernel 2.6.20-16-generic
2 root		(hd0,0)
3 kernel		/boot/vmlinuz-2.6.20-16-generic 4 root=UUID=aec8bcb8-510a-453d-8e59-b9c0f8339786 ro quiet splash
5 initrd		/boot/initrd.img-2.6.20-16-generic
6 quiet
7 savedefault
```

Line 4 needs to read UUID=aec8bcb8-510a-453d-8e59-b9c0f8339786 ro vga=791 for it to boot properly
just a bit confused on where exaltcy to put this line

---

