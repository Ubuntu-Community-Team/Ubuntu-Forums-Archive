---
title: "still can't get ATI drivers to work."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-08
OK, i have been following this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

and the 3 times i have tried to install it, i have failed. I need help real badly.
I have followed every step, then when verify it, this is what it says

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I have a Radeon All In Wonder x800, and this is being a real pain for me, tell me if you need any other specific details, i will post them.

---

### Post by phinn on 2007-05-08
Thats really strange, I couldn't get them to work with 2.6.20 for all through Feisty alpha until I reinstall the final version and did this:

(you don't need to install this with ubuntu but I use kubuntu)
sudo aptitude install restricted-manager
sudo restricted-manager

then just enabled the drivers.

After a reboot it worked!

---

### Post by simplekin on 2007-05-08
> **phinn said:**
> Thats really strange, I couldn't get them to work with 2.6.20 for all through Feisty alpha until I reinstall the final version and did this:

(you don't need to install this with ubuntu but I use kubuntu)
sudo aptitude install restricted-manager
sudo restricted-manager

then just enabled the drivers.

After a reboot it worked!

tried that still get this


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

