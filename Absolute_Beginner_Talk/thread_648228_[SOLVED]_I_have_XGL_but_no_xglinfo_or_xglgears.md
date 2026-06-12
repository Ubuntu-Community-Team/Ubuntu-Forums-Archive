---
title: "[SOLVED] I have XGL but no xglinfo or xglgears?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-23
I followed this [http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz)

XGL is installed but no xglinfo or gears?

**EDIT**
Well, I stumbled upon a fix for this, somehow.

I assumed it was the xorg.conf but didnt check it I just thought it needed updating, so I did

> sudo dpkg-reconfigure -phigh xserver-xorg

This caused the problem that it set the driver back to ATI from fglrx...(?)

So I edited the xorg.conf ( 'gksu gedit /etc/X11/xorg.conf' )back to fglrx from the backup that was automatically made due to the update.

And now glxinfo is there.

So its solved....by a complete fluke. :)

I still have no direct rendering but thats another story, lol.

---

### Post by MangasColoradas on 2007-12-23
LOL, its glxinfo isnt it? :lolflag:

How embarrasing!

---

