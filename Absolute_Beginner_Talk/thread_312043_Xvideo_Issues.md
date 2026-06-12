---
title: "Xvideo Issues"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by marcusgleason on 2006-12-03
Whenever I try to open a .wmv file, I get the following error:

"It seems there is no Xvideo support for your video card available.  Run 'xvinfo' to verify its xv support and read DOCS/HTML/en/video.html#xv!  See 'mplayer -vo help' for other (non-xv) video out drivers.  Try -vo x11."  

I run xvinfo and get this:

X-Video Extension version 2.2
screen #0
 no adaptors present

What do I do?  I have no idea where DOCS/HTML/en/video.html#xv is.  Please help!!

---

### Post by ecor6633 on 2008-02-27
I have the same problem and if i would like to get this working i can at least explain what i understood so that anybody can help us both.

It seems our X server hasn't enabled Xvideo also called xv. To solve your problem, you may try "mplayer -vo x11 file.wmv" it worked for me.

But how can we enable this xv ?

I had a look to another computer's xorg.conf and added the same Module section so that mine looks like that :
Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "ddc"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
EndSection

But as i am using nv driver on this computer and i810 on the other i'm not sure the problem is not in that section :
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8600M GS]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

If anybody can help me understand the problem, any help would be appreciated.

Thanks

---

