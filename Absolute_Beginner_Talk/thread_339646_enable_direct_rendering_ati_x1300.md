---
title: "enable direct rendering ati x1300"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by lilmienboy on 2007-01-16
i've been trying to find how to enable direct rendering for hours, still no result. here is my information:
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

 glxinfo | grep rendering
direct rendering: No

i have a dell inspiron ati x1300 with ubuntu edgy if that help 

thanks for the future

---

### Post by Shatrat on 2007-01-16
There are lots of how-to pages out there for installing the ATI drivers.
Here is one you might try.
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Don't forget to configure your /etc/X11/xorg.conf to use the "fglrx" driver instead of the "ati" driver in the "Device" section.

Good luck, the drivers are the reason I got rid of my ATI card and got an nVidia.

---

### Post by lilmienboy on 2007-01-16
thanks for the help still kind of lost tho

---

