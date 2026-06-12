---
title: "no desktop effects"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-09
when i try to enable desktop effects,it simply fails,with a window saying that the effects could not be enabled,i had downloaded all the updates as prompted after installation.my PC  does not have any special graphics card except the one that comes customarily.how can i enable the desktop effects.

---

### Post by glennric on 2008-03-09
More specifically what video card do you have?  To find out try
```
lspci | grep VGA
```
or just
```
lspci
```
It is possible that your video card is blacklisted by compiz.  In this case you may not be able to use compiz.  Try running 
```
compiz --replace &
```
from a terminal and see what output that gives you.

---

### Post by staticvoid on 2008-03-09
ussually graphics cards do not come customarily...

is it intel? nvidia? ati?

It would be good to have that info.

Next step would be to check what driver you are using, and then use the better one... its pretty simple...

what you see on the screen is provided by a desktop enviorment and Xorg.

in your config file (xorg.conf) you just tell it what driver to use after you install the driver

Heres a howto: [http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

good luck!  :D  its great to know how your computer works, eh?

---

