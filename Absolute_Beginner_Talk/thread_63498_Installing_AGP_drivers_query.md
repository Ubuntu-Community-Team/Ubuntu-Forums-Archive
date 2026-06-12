---
title: "Installing AGP drivers query"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by thepcdoctor on 2005-09-08
I have ATI 9800pro graphics card. I installed drivers by following instructions on [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI), but checking gives this:
theboss@ubuntu:~$ fglrxinfo
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I'm guessing that it didn't work. I thought l'd have another go at it with following command line given on another post: $ sudo apt-get install linux-restricted-modules-<your-kernel-version> xorg-driver-fglrx?  Would this fix it?
Is this command the same as sudo apt-get install xorg-driver-fglrx?
If I use this, how do I find my kernal version?

Another question- when I click the upgrades available icon there are hundreds of entries. Should I just select them all? If not, how do I know what's essential?

---

### Post by thepcdoctor on 2005-09-09
Can anyone help me here??

---

