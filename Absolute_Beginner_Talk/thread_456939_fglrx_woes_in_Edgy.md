---
title: "fglrx woes in Edgy"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by darkmage77 on 2007-05-28
OK, so far my first Ubuntu install has gone very well. But I have run into a problem that I see a lot of other people are having: ATI and Linux have a stormy relationship.

Here's my problem. I'm running Edgy on an Abit NF7-S2G with an AthlonXP 3000+. This is an nForce2 Ultra400 chipset. I have an ATI X1650 AGP video card. When I installed the latest fglrx through Synaptic, I was able to get a better screen res (1280x1030) than at the fresh install. But when I used fglrxinfo, I got:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Correct me if I'm wrong, but I believe if fglrx is installed, then ATI should be in there somewhere. I read on the Unofficial ATI Linux wiki ([http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)) that nForce3 chipsets had trouble with ATI cards. I'm not sure what that means for nForce2, but I do know that from what I've seen so far I can't install install nForce2 drivers without uninstalling fglrx.

Am I wrong? Could there possibly be an easier way to enable my (trash) card? Someone please help!

I've already followed the guide in the Beginner sticky even though I'm in Edgy, and I've also done the first 2 commands on the wiki page listed above. When I grep I get this:

fglrx                 406988  0 
agpgart                34888  2 fglrx,nvidia_agp

---

### Post by darkmage77 on 2007-05-29
Dunno how appropriate this is, but...

bump

---

