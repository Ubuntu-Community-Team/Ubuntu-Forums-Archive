---
title: "server install xwindow problems"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by zenkoanlife on 2006-05-07
I just installed 5.10 on an old machine with hope of making a server. I am now trying to add fluxbox and have a problem with the x window system. when I type startx I get a few screen flashes and end up back at the terminal with the following output....

skipping "/usr/X11R6/lib/modules.libfb.a:fbmmx.o": no symbols found
Warning: font renderer for "pcf" already registered at priority 0
about a dozen more Warning: font renderer ....etc. lines

Is there something else I should be installing, and/or some configurations I need to do? so far the only things i've installed with apt are fluxbox, xdm and x-window-system-core.

---

### Post by blair on 2006-05-14
I'm no expert here, but this could be a simple monitor or video card config problem. Suggest running through the X config process:

sudo dpkg-reconfigure xserver-xorg

if it doesn't work the first time, retry it again using different settings. For example, set it up for 640x480 only. If that works, then retry with 800x600. If it doesn't work, try different settings at 800x600 until you find the right magic combo.

---

### Post by zenkoanlife on 2006-05-16
okay, so I manually installed fluxbox and when I type ./configure i get an error

configure: error: Fluxbox requires the X Window System libraries and headers.

what am I missing?!

---

### Post by w1z4rd on 2006-06-21
This should help you out

```
sudo apt-get install xlibs-dev    
```

---

