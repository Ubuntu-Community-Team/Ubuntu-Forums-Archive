---
title: "Can i change this screen?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-27
Is it possible to change this screen to a simple progress bar for example?

[IMG]http://shots.osdir.com/slideshows/430_or/1.png[/IMG]

---

### Post by gibson on 2006-02-27
> sudo gedit /boot/grub/menu.lst

then find the line

> kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda4 ro quiet splash

and change

> kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda4 ro quiet vga=788

that is what i do.

you dont get the annoying splash screen and you get a nice list of what the os is doing on startup... ps if i am not mistaken 788 is for 1024x768... but i actually use 791 for 1280x1024

hope to help

---

