---
title: "Firefox crashes feisty and reverts to login screen"
date: 2007-05-14
forum: Apple PPC Users
---

### Post by m_i_k_e on 2007-05-14
Is anyone else having this problem?  It happens mostly when I close a tab or window.

---

### Post by Gen2ly on 2007-05-14
eeek, sound awful!  I would guess thats its missed a needed component.  Run Firefox from the command line and see if you can catch it's output.

---

### Post by stmiller on 2007-05-14
I've had this a couple of times. It crashes X (not feisty). Check the xorg logs perhaps.

---

### Post by stmiller on 2007-05-19
X crashes for me when dri and glx is enabled. I commented those out in

/etc/X11/xorg.conf 

like this:

```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#        Load   "dri"
        Load    "extmod"
        Load    "freetype"
#       Load    "glx"
        Load    "int10"
        Load    "vbe"

```

No 3D, but at least it is stable.

---

### Post by 3rdalbum on 2007-05-19
I had a similar problem with GPLFlash installed - Flash movies were causing Firefox to crash, but the crashes were due to problems with X. Do you have any Flash support installed?

---

### Post by bipco on 2007-05-19
I've had it repeatedly - with Firefox, Epiphany and Galeon - I've just completely uninstalled them all and all the plugin stuff I could see - now I've re-installed just Firefox, waiting to see what happens.

Did seem to happen more on sites with lots of multimedia stuff - so maybe a plugin thing. The first sign was a slowing down/lagging of the mouse pointer.

---

### Post by bipco on 2007-05-22
Further to this - uninstalling and re-installing without any plugins or addons does seem to have sorted it out for me. Not got round to trying re-installing anything to try and track it down yet. However, Firefox has some other problems on my machine (Lombard Powerbook) - if I customize the toolbars, the menus don't work after that until I restart Firefox. Also my bookmarks toolbar is not showing any bookmarks, despite there being some added to it.

---

