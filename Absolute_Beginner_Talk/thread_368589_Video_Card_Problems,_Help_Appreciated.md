---
title: "Video Card Problems, Help Appreciated"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by barabaskid on 2007-02-23
Hello,

Beginner here, wanted to see if anyone could help me with my problem. I just had to alter my system with "$ sudo dpkg-reconfigure xserver-xorg" in rescue mode, and reset my graphics card (Intel Corporation 82852/855GM Integrated Graphics Device) to the "vesa" setting on the first screen. My resolution is fine, but the screen is rather jerky when I scroll in a window, and video seems to lag a quarter of a second behind what it should be.

I ran "glxinfo | grep rendering" to see if it was a rendering issue, and got:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No


So I think direct rendering and 3d rendering may be turned off. My questions:

1. Should I switch the xserver-xorg to the i810 choice. If I do, will that fix the rendering automatically? And if I should change to i810, can I do that that in the terminal, or do I have to use rescue mode?

and

2. If I should keep vesa, how do I enable direct and 3d rendering?

As I said, bit of a newbie here, so any help is appreciated. Thanks much, everyone.

BarabasKid

---

### Post by Shatrat on 2007-02-23
You will need the intel driver to get direct rendering with your graphics chipset.
You can use the i810 driver either by using sudo dpkg-reconfigure xserver-xorg and choosing it in the menu or by editing your /etc/X11/xorg.conf and changing the driver in the device section from "vesa" to "i810"

---

