---
title: "Display and Font Size"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-06-09
after installing dapper drake server, the display is larger than my 19 inch screen.  also the font size is too big.  Does anyone know how to use command line to set the display/font size.  

Thanks.

---

### Post by ggaaron on 2007-06-09
Size can be adjusted in /etc/X11/xorg.conf you'll find resolutions to use there, use nano, or if you can vim/emacs. With fonts there can be many problems - this could be just too big font  - for example 20 instead of 12, but dpi can be wrong also, I had to use this:
echo 'Xft.dpi:90' | xrdb -merge
but you have to have a running xserver and it only affects newly run applications - I know how to do this in kdm to work and if you want use startx, but I don't know how to run this in gdm.

---

### Post by ggaaron on 2007-06-09
Aghh - server, then you probably don't have x on.

If it's too big then use your monitor to auto adjust, I don't know a software way.

I don't know if you can change font size, but you can configure framebuffer to have for example 1024x768, not default 640x480.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

Use this guide.

---

