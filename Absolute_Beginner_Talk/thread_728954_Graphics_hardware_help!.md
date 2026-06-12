---
title: "Graphics hardware help!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by ryuaced on 2008-03-19
Hi, 
I am really new to linux 
and installed ubuntu and it worked fine,
but my ati card hardware wouldnt accept properly
and anytime i activated it it would restart than start up
in low graphics mode, 
than i tried to force it to start up without low graphics mode 
and now the screen is fuzzy and scrunched and basically 
unable to be read, i can use functions and open up 
the terminal but basically more by memory,
it reminds me of an Old nintendo when you didnt
quite push the cartridge in JUST right,
 it was all blurry and blocky but yeah,
basically i just need a commandline or sudo
to run in the terminal that will boot up in low graphics mode
so i can turn off my ati hardware or a way to use the linux generic
instead.
Thanks for reading!

---

### Post by justleen on 2008-03-19
when in a terminal, you can issue 
```
 sudo dpkg-reconfigure xserver-xorg -phigh 
```
This will reconfigure the Xserver settings
go through the option, make sure to select the VESA driver. once done, restart gnome 
```
 sudo /etc/init.d/gdm restart 
```This should give you a normal readable X  again...

---

### Post by NR1224 on 2008-03-19
you can also try cntrl+alt+backspace, i believe it resets the x-windows plugin

---

### Post by (((X))) on 2008-03-19
Every time I run in trouble with videocards I run
dpkg-reconfigure -phigh xserver-xorg in terminal.
If there will be no effect, take -phigh away.
Easier  than editing xorg.conf manually

---

### Post by ryuaced on 2008-03-19
thanks ! life savers for sure!!

---

