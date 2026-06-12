---
title: "USB problems"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by dangibson30 on 2007-07-04
my mp3 player or camera wont mount, wondering if anyon can help me out, when i try and mount it gives me this message:

root@dan-desktop: mount /mnt/usb
mount: special device /dev/sda1 does not exist

also does anyone know how to change keyboard settings in fluxbox, any help will be much appreciated, thanks

---

### Post by diatribe on 2007-07-04
after you plug it in type dmesg and see what it is listed as, then try mounting that

---

### Post by RedSquirrel on 2007-07-04
> **dangibson30 said:**
> my mp3 player or camera wont mount, wondering if anyon can help me out, when i try and mount it gives me this message:

root@dan-desktop: mount /mnt/usb
mount: special device /dev/sda1 does not exist

It looks like the device is not being detected for some reason. On my system, when I use my USB memory stick, the /dev/sda1 is created automatically and I can manually mount on /media/storengo (a mount point I created myself). Does anything else mount using that USB port?

What does this report?

```
ls -l /dev/sda*
```
> **dangibson30 said:**
>  also does anyone know how to change keyboard settings in fluxbox, any help will be much appreciated, thanks

What do you mean by "keyboard settings"? General keyboard settings are in /etc/X11/xorg.conf.

Shortcut keys are set in ~/.fluxbox/keys.

[http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts)

You can also try fluxconf. It's a graphical program to help you make keyboard shortcuts. It's in the repositories.

---

