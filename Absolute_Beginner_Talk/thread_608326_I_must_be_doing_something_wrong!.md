---
title: "I must be doing something wrong!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by TurboABA on 2007-11-09
Alright... so I managed to install Xubuntu on my amazing TP 600e.
I've done lots of searches and found lots of useful information on thigs that need to be edited, changed, etc to get the proper video display, sound and network setting.

I have all this info, yet I can't manage to do the simplest thing!

I'm trying to edit the file XORG.CONF for my display settings, and I can't do anything.  I can't even use the edit command.  I can browse around (using terminal) but that's about it.

Can someone please point me in the right direction?

All I'm trying to do for starters is set my default color from 24bit to 16bit to work with my amazing video card.  Please keep in mind that I've never used Linux prior to today (at least not the terminal and commands).

Any help is appreciated.

---

### Post by PurposeOfReason on 2007-11-09
You're probably browsing the file as a normal user, you need to be root. In the terminal run


sudo nano /etc/X11/xorg.conf

Nano can be replaced with your text editor.

---

### Post by overdrank on 2007-11-09
Hi just to add to PurposeOfReason
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
Good luck!:KS

---

### Post by rsambuca on 2007-11-09
A graphical based text editor would be:```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by TurboABA on 2007-11-09
> **PurposeOfReason said:**
> You're probably browsing the file as a normal user, you need to be root. In the terminal run


sudo nano /etc/X11/xorg.conf

Nano can be replaced with your text editor.


I'm an IDIOT.

I was trying to use gedit instead of nano.  I've managed my first change.  Thanks.

---

### Post by PurposeOfReason on 2007-11-09
> **TurboABA said:**
> I'm an IDIOT.

I was trying to use gedit instead of nano.  I've managed my first change.  Thanks.

No, that's perfectly fine to use gedit (I just didn't know if Xubuntu came with it :/). It's all about the sudo part.

---

### Post by TurboABA on 2007-11-09
From what I understand at this point (and I could very well be wrong) Xubuntu doesn't come with the graphical editor.  I'm actually typing from the "said" laptop at the moment.  I've managed to change a few things so far and even connect to the network (wire at the moment).  I will work on trying to enable the wireless card shortly.

I am astonished at the kind of speed this dinosaur is capable of downloading files at.  I just had it downloading another copy of UBUNTU at 950k/s.....   I was shocked.

I'm starting to like this os already.

---

### Post by overdrank on 2007-11-09
> **TurboABA said:**
> From what I understand at this point (and I could very well be wrong) Xubuntu doesn't come with the graphical editor.  I'm actually typing from the "said" laptop at the moment.  I've managed to change a few things so far and even connect to the network (wire at the moment).  I will work on trying to enable the wireless card shortly.

I am astonished at the kind of speed this dinosaur is capable of downloading files at.  I just had it downloading another copy of UBUNTU at 950k/s.....   I was shocked.

I'm starting to like this os already.

HI and I believe that gedit started with feisty and onward in xubuntu and also you can use mousepad in xfce. :KS

---

