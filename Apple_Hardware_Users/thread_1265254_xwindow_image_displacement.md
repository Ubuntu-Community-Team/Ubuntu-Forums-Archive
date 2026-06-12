---
title: "xwindow image displacement"
date: 2009-09-13
forum: Apple Hardware Users
---

### Post by edmundus on 2009-09-13
Hallo,
I'm using Ubuntu 9.04 on an eMac PowerMac6,4 PowerPC G4 (1.2).
It work fine with 1 exception:
The xwindow is displaced to the left by about 1 cm and I don't see the whole display.
I tried other slutions and installed Fedora and Suse.
The problem remained so I got back to Ubuntu which I like.
But what can I do?
In one of my old Linux book they sugested to use xvidtune for such problem.
However xvidtune don't work with Xorg.
Any idea what I can do?
Please remenber that the eMac don't have buttons in the front for controlling the display.
Thank you.

Edmund

---

### Post by sweetleaf on 2009-09-15
xvidtune wouldn't run on my iMac G3, either.* I had to specify a modeline in my /etc/X11/xorg.conf, and then make manual adjustments to the first (horizontal) set of numbers. This was a time-consuming process, because I had to adjust, restart X, see what happened, adjust, restart X, etc. Let me know if you want to try this, and I can post more details. Note that this only fixed the video display in X; the console screens are still offset and partly unreadable.

*Eventually, xvidtune DID start working for me. So the problem isn't with Xorg. Unfortunately, I don't know what changed to make it work.

---

### Post by edmundus on 2009-09-26
hy sweetleaf

thank you for your reply and please let me apologise for aswering so late.
I read about your solution in my Linux bible. It's a long way and besides you correct only the X display. 
I'm looking for a general solution.
By the way, why does this happen? I mean I tried several distibutions and the same problem happened.
Anyway I'll try the xvidtune again.

edmundus

> **sweetleaf said:**
> xvidtune wouldn't run on my iMac G3, either.* I had to specify a modeline in my /etc/X11/xorg.conf, and then make manual adjustments to the first (horizontal) set of numbers. This was a time-consuming process, because I had to adjust, restart X, see what happened, adjust, restart X, etc. Let me know if you want to try this, and I can post more details. Note that this only fixed the video display in X; the console screens are still offset and partly unreadable.

*Eventually, xvidtune DID start working for me. So the problem isn't with Xorg. Unfortunately, I don't know what changed to make it work.

---

### Post by sweetleaf on 2009-09-26
> **edmundus said:**
> By the way, why does this happen? I mean I tried several distibutions and the same problem happened.

Presumably, most people with Apple hardware run an Apple operating system, so they can use Apple's software tool for making and remembering monitor adjustments. In the wider computer hardware world, most monitors have external buttons, so there isn't much need or demand for developing such a tool for Linux.

---

