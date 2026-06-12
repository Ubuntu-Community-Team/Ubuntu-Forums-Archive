---
title: "Dell Laptop &amp; TV Out, Dual Display Problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-03-03
I just installed the os and xfce on my old dell laptop. I am currently using xfce. I tried setting up multiple display with Display under System. I had the s-video pluged into my laptop and the tv. The laptop had a display of 1600x1200 and the tv had a solution of 800x600. I restarted, and there were no picture on the tv and the laptop resolution was set at 800x600. So, I restarted my laptop after setting up the corrent resolution and disabling the tv output. Then, I had my native resolution back and tried setting up dual head mode again. I set the laptop for 1600x1200 lcd and the tv again to 800x600 crt, because there were no resolution for tvs. Then restarted the laptop, but then I was sent to the terminal (shell) interface. the system old me the x server failed. It asked me if I wanted to see the details of the failure and then asked me if I wanted to try refiguring the settings, but that failed as well.

So, I loged into my user through the shell. cd to /etc/X11/ and nano xorg.conf. I found out that it tried to show both displays. I had a screen0 and screen1. I tried manaual editing the xorg.conf after making a back up of the xorg.conf. But after rebooting, I still had problems with the gui.

So, my question is, how do I manual edit the xorg.conf file to get back to default, because I only have one xorg.conf. Or should I just start over and rewrite the whole thing. Is there like a default format for the xorg.conf?

Specs:
Xfce
Nvidia
P3 1.13 Ghz
512 DDR
S-Video Port
1600x1200

Sorry for the long post, but thanks
Sugi
_____________

---

### Post by Sugi on 2008-03-03
Bump

---

### Post by Sugi on 2008-03-03
Bump

---

### Post by Sugi on 2008-03-04
Bump

---

### Post by Sugi on 2008-03-19
Bump

---

### Post by Sugi on 2008-03-20
Bump

---

### Post by Sugi on 2008-03-24
Bump

---

