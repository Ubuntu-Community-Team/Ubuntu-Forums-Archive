---
title: "Broken X with unsuccessful ATI driver install"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by myattb on 2007-07-07
I have broken X with a failed ATI driver install (attempting to enable TV Out).
The bottom section of my screen containing AVN now just appears black (see attachment)
I did break it completely (X would not event start) but I managed to reinstate a previous version of /etc/X11/xorg.conf.

I am not sure what to do to fix this or even what is now wrong?

Any help much appreciated.

---

### Post by kosmic on 2007-07-07
Hi in a Terminal just type the following :


sudo dpkg-reconfigure xserver-xorg


Then just answer the question and you should have X again ;)

---

### Post by myattb on 2007-07-08
Excellent thanks...
I am now back to the open source ATI drivers for my radeon 9000 card and X is working as before.
However, is it possible to get TV Out working with these drivers or do I need to ATI proprietry drivers to get this functionality?

---

### Post by BL00dFox on 2007-07-08
> **myattb said:**
> Excellent thanks...
I am now back to the open source ATI drivers for my radeon 9000 card and X is working as before.
However, is it possible to get TV Out working with these drivers or do I need to ATI proprietry drivers to get this functionality?

I recommend you download the drivers from ATI's website and use the aticonfig tool to get your TV-OUT working.

Good Luck

---

### Post by pyros on 2007-07-08
> **myattb said:**
> Excellent thanks...
I am now back to the open source ATI drivers for my radeon 9000 card and X is working as before.
However, is it possible to get TV Out working with these drivers or do I need to ATI proprietry drivers to get this functionality?

You might try this howto that I found (somewhere?) on the forum:
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

Unfortunatly, I have no tv out on my card, so I haven't been able to test it.

---

