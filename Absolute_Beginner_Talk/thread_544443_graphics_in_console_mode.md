---
title: "graphics in console mode"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-09-06
apparently, it is possible to do this with mplayer and links2 (and other stuff, i guess). when i tried *links2 -g*, it looked like i didn't have any /dev/fb0 device (whatever that means). is there a simple way to get this going? what about viewing .jpg and .png images?

why do i want to do this? just think how cool my neighbors will think i am.

btw, watching video clips with *mplayer -vo caca* is pretty silly. i guess that's how the world appears to someone like daredevil.

---

### Post by macogw on 2007-09-06
You need to turn on the framebuffer. 
```
gksu gedit /boot/grub/menu.lst
``` and at the end of 
> # defoptions=quiet splash
add > vga=x where x is a framebuffer setting that your screen can use.  I use 791 for high-color 1024x768

---

### Post by justin whitaker on 2007-09-06
Try FEH.

[http://linuxbrit.co.uk/feh/](http://linuxbrit.co.uk/feh/)

Tons of nifty features.

[http://linuxbrit.co.uk/feh/wiki/FehFeatures](http://linuxbrit.co.uk/feh/wiki/FehFeatures)

---

### Post by Steveway on 2007-09-06
You need to run a Xserver for links -g.

---

### Post by fuscia on 2007-09-06
> **macogw said:**
> add  where x is a framebuffer setting that your screen can use.  I use 791 for high-color 1024x768

where would i do this part?

---

### Post by meborc on 2007-09-06
> **macogw said:**
> ...where x is a framebuffer setting that your screen can use.  I use 791 for high-color 1024x768
my laptop uses 1024x768 with high colors in x server... BUT when i change the line to include vga=791, i get nothing... just black screen until my login appears...

now i know it is possible, to get that resolution without x... i have used 773 option before... but now it seems not to work either... am i doing something wrong? should i modify the defaultxxx line AND the kernel line? 

thanks in advance (i really hate the usplash, and would like to see some text... NOT in 800x600 or whatever the default is in my laptop) :D

---

### Post by SOULRiDER on 2007-09-06
> **Steveway said:**
> You need to run a Xserver for links -g.

No you dont, you can still run it from a console.

> **fuscia said:**
> where would i do this part?
/boot/grub/menu.lst in the line where it has all the options like splash and quiet, just add it at the end.

I use links in Gentoo and Arch when I dont have a DE. To make it run you need to make sure your user can use a framebuffer device and also that you have the GPM daemon running.

---

### Post by Steveway on 2007-09-06
Yes, sorry.
So you need either a Xserver or you need to use the Framebuffer.

---

