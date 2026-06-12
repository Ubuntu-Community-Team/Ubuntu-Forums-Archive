---
title: "Direct Rendering Help"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by GorillaDilla on 2007-07-08
Hello, I am new to Linux, and i need to turn on my Direct Rendering, or just to get it working with sglrx driver. My video card is an x700 Radeon Pro. I have the fglrx driver installed, and am running Ubuntu 7.04 Feisty. Does soemthing need to be changed in my xorg.cons? I have the driver installed, but i can not get direct rendering working.

---

### Post by LostArt on 2007-07-08
I have an ATI card as well, and all that I have to say is that ATI and Ubuntu, especially for direct rendering are very very very annoying, I'll try to do a search on google for you later though


Edit:

Okay I had some free time, way sooner then I thought, this is what I dug up with a quick google search

Check out this website

[http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/)


and you might try adding this to the end of your xorg.conf


Section "Extensions"
        Option "Composite" "false"
EndSection

and I got this info from this forum

[http://www.linuxquestions.org/questions/showthread.php?t=535210](http://www.linuxquestions.org/questions/showthread.php?t=535210)




hopefully this'll work for you

---

### Post by Vajra Vrtti on 2007-07-08
See the [Unofficial ATI Linux driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide").

---

