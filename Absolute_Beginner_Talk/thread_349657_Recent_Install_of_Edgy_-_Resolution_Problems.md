---
title: "Recent Install of Edgy - Resolution Problems"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Rinulin on 2007-01-30
I recently installed Edgy Eft on my desktop. Now, when I start the system, my screen resolution is set to 1024X768 - and that is the highest resolution I can set it too. How can I get the screen resolution higher?

---

### Post by taurus on 2007-01-30
Maybe you need to install a driver for your graphic card first before you can go higher resolutions.  What is your graphic card anyway?

---

### Post by Rinulin on 2007-01-30
I'm pretty sure that I updated the driver once I noticed the problem.

I have an Nvidia GeForce 7900GS

---

### Post by taurus on 2007-01-30
Look in /etc/X11/xorg.conf and see which "Driver" it is using.

Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```
If it says "nv", then you are just using the generic driver for your nVidia card.  In that case, you need to install nVidia driver for it.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

