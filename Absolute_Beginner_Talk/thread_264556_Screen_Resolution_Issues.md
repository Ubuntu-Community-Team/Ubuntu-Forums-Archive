---
title: "Screen Resolution Issues"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by ryn on 2006-09-24
The screen resolution option in the systems panel does not offer me an option of changing my resolution from 640x480 to anything else.
Any ideas how I can make a change to the resolution...it is a pain to navigate pages with this resolution!!

---

### Post by croak77 on 2006-09-24
In /etc/X11/xorg.conf.

---

### Post by PriceChild on 2006-09-24
Sounds like you'll need to reconfigure your X...
```
sudo dpkg-reconfigure xserver-xorg
```Leave all the options as they are if you don't understand it.

When you get to choose availiable resolutions, spacebar checks them, and enter moves onto the next page!

BTW this is an easier method to edit your xorg.conf

---

