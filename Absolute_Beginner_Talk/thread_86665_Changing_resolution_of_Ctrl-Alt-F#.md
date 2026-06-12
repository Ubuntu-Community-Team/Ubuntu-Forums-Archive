---
title: "Changing resolution of Ctrl-Alt-F#"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by milpool on 2005-11-06
I would like to know how I can change the resolution of my Ctrl-Alt-F# 1 - 6 screens. I am sorry that I do not know the technical name for these screens. Any help would be greatly appreciated

Thank You

---

### Post by kairu0 on 2005-11-06
You're asking how to use the console framebuffer.

That would be your grub configuration. You need to add a parameter stating "vga=xxxx" (you'll need to choose which xxxx is right for you.)

               640x480  800x600    1024x768 1280x1024
8 bits      vga=769   vga=771   vga=773 vga=775
16 bits    vga=785   vga=788   vga=791 vga=794
32 bits    vga=786   vga=789   vga=792 vga=795

So, reboot, push E on the OS selection screen to change your parameters, then add the vga=xxxx liine to the line with the other parameters on the next screen. Let your machine boot, and if you like the new mode, then add it to /boot/grub/menu.lst. If you don't like it, repeat process with a different xxxx number.

---

