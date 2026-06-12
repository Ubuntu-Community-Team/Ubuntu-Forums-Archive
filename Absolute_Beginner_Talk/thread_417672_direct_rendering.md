---
title: "direct rendering"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by stickperson on 2007-04-21
Hey, I have a Thinkpad T60 which has a ATI x1400 video card.  For some reason I cannot get direct rendering to work.  I tried so many guides, reconfigured stuff and all.  Does anyone know exactly how to do it?  Thanks

---

### Post by DougieFresh4U on 2007-04-21
The only way I was ever able to get DRI to work on both my Intel machines was to change the depth from 24 to 16 inthe x file. Don't know if that can help:confused:

---

### Post by stickperson on 2007-04-21
> **DougieFresh4U said:**
> The only way I was ever able to get DRI to work on both my Intel machines was to change the depth from 24 to 16 inthe x file. Don't know if that can help:confused:

wait, where at? can you paste that section?  thanks

---

### Post by DougieFresh4U on 2007-04-21
I can not promise it will work for every one but here you go:;
Code:

sudo nano -Bw /etc/X11/xorg.conf

and change the Depth from 24 to 16. Save it with <Ctrl>o and <Ctrl>x. Then, restart X again with <Ctrl><Alt>Backspace or reboot.

---

### Post by stickperson on 2007-04-21
what depth?  there are a couple of different things.. screen depth, display depth a couple of times...

---

### Post by DougieFresh4U on 2007-04-21
> **stickperson said:**
> what depth?  there are a couple of different things.. screen depth, display depth a couple of times...

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810 CGC [Chipset Graphics Controller]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"

---

### Post by stickperson on 2007-04-22
Hm, that just messed up my whole file so I had to reconfigure it.  No big deal though.

---

### Post by stickperson on 2007-04-22
Ok, I got direct rendering enabled, followed directions to install beryl, but when I run it and select beryl from the select window manager screen, this pops up in terminal.  

** (beryl-manager : 3233) critical **: can't execute beryl-xgl: success

---

