---
title: "Aaah! Mouse won't move correctly!"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by Slip the Lips on 2009-11-15
Hi. I have a Late 2008 model MacBook.  I dual-booted Snow Leopard and Jaunty together recently, and the mouse has been bothering me a lot. The trackpad won't correctly move. On the Mac side, when you move your finger in a circle on the trackpad, the mouse freely moves, and it is a bigger circle, so it's faster to get from one side of the screen to another. In Ubuntu, it doesn't move as freely, and it doesn't move as big, so it takes a good 6-7 swipes of the finger to make the mouse cross the screen. I've been looking around the internet to see if anyone else has this problem, but it seems to me that it's only me. Can I run the "BootCamp Driver" disk under Wine and will that fix these problems? Thanks for your time.

---

### Post by tom4everitt on 2009-11-15
There is actually quite a lot of info on google. Google 

"trackpad sensitivity ubuntu"

"touchpad acceleration ubuntu"

or some mixture of above. Most of them refer to the file /etc/X11/xorg.conf where you're supposed to be able to change the parameters minspeed and maxspeed. I'm not sure this file is still relevant, have a vague memory of it being replaced by something else. Might be worth a shot at any rate. 

There is nothing in the GUI? System -> preferences -> touchpad 

or something like that

---

### Post by linuxopjemac on 2009-11-16
you can install a touchpad preference program, don't remember the name though...just search "touchpad" in synaptic, you'll find what I mean.

---

