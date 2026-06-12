---
title: "Troubles configuring ATI driver..."
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by lg3 on 2006-04-21
Ok followed this [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide")
and double checked my work and here is the output which isn't what it should be:

leroy@user2:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

What do I need to do next to get it recognize my ATI driver? I have run through the above link 2x. 

Appreciate the help.

---

### Post by ZiLOG_Z80 on 2006-05-06
Which driver did you install, the one provided by ubuntu or the one from ati?

Either way I'm not entirely sure what the problem is if you did ```
$ sudo dpkg-reconfigure xserver-xorg
``` and selected the fglrx driver

I had succes with the ati driver and following this HOWTO

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")

---

### Post by adam.tropics on 2006-05-07
Also, as stated on the wiki page, be aware of conflicts with madwifi etc....

---

