---
title: "Ubuntu 7.10 No video card"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by vivisectionnnn on 2008-02-28
tried to install ubuntu with ati x1300 video card but kept freezing up in gnome manager.

reinstalled it without video card and Just booted up ubuntu 7.10 using only my onboard VGA. finished installation, updated all files. now i have no clue how to set up the driver for an ati x1300.

tried several forum tutorials but none match my problem. have no xorg directory.

anyone think they could walk me through this ?

---

### Post by Arthur Archnix on 2008-02-28
You should still have xorg installed, it's what creates that nice desktop. Right now xorg is using your onboard graphics controller, but it could probably be made to use your video card (I say probably because ATI can sometimes be nasty).

Plug in the video card and reboot. If you're lucky, the desktop will come up and offer you the opportunity to use restricted drivers for this device (the video card). 

If that doesn't happen but the desktop does come up, open up a terminal and type these commands. When you paste the output back here, be sure to wrap it in code, that is, highlight the output then click the code tag above (looks like this -->#). These are the commands, there are three:
```
lspci
lsmod
cat /etc/X11/xorg.conf
```

The first one says, what hardware can Ubuntu see attached to my computer?
The second one says, what drivers has Ubuntu loaded to use this hardware?
The third one says, what is my current xorg setup?

---

### Post by Crafty Kisses on 2008-02-28
Have you tried looking at the **Restricted Drivers Manager.**

---

