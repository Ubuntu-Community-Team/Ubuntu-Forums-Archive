---
title: "[SOLVED] Hardy on eMac"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by kerryhall on 2008-12-18
So I did the Hardy PPC alternate installer on my eMac. After install, I see the Ubuntu splash screen, then nothing. I can ctrl alt f1 to a terminal, and I assume I need to manually edit my x.org file?

What modifications do I need to make to that file?

Thanks!

---

### Post by macintosh on 2008-12-18
I would recommend reinstalling that's all. You then see if you get any further?

---

### Post by kerryhall on 2008-12-18
Installation completed though.

---

### Post by kerryhall on 2008-12-18
I seem to have fixed the problem by using the "fbdev" driver, but I guess this doesn't have hardware acceleration.

Does anyone know how to get the ATI driver to work?

---

### Post by albinootje on 2008-12-18
> **kerryhall said:**
> I seem to have fixed the problem by using the "fbdev" driver, but I guess this doesn't have hardware acceleration.

Does anyone know how to get the ATI driver to work?

Did you check -> System -> Administration -> Hardware Drivers ?

This might help : [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

And this : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/196129](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/196129)

mentions the boot option : video=ofonly
which i vaguely remember from a Debian install on an apple iBook years ago.

---

### Post by kerryhall on 2008-12-18
Yes, I tried that. I am using a PPC eMac. I am giving Envy a try right now, but doubt it will work.

---

### Post by albinootje on 2008-12-18
> **kerryhall said:**
> Yes, I tried that. I am using a PPC eMac. I am giving Envy a try right now, but doubt it will work.
hmmm :(
Did you try this 
```
site:ubuntuforums.org emac
```
in a search-engine ?
Good luck!

---

### Post by kerryhall on 2008-12-18
Yes, I tried searching for all kinds of things. I followed a guide given by user crapple here:

[http://ubuntuforums.org/showthread.php?t=964032](http://ubuntuforums.org/showthread.php?t=964032)

but it looks like OpenGL acceleration is choppy at best. Any ideas?

---

### Post by mkvnmtr on 2008-12-19
Just so you know on my G4 IBook I have never been able to get Open GL to work very good. Some times a game will open but most of the time they won't. It was never important enough to me to try to see if I could fix it.

---

### Post by kerryhall on 2008-12-19
I am going to close this thread because I am going to start a new one with a much more descriptive title, after working on this problem for over six hours last night.

---

