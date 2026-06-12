---
title: "Touchpad + Tablet"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by bren21 on 2007-03-30
Okay, after a couple hours of looking through tutorials and such, I finally managed to get my Wacom Graphire 4 tablet to work. Well, I use it on a laptop, so when I am moving my laptop around I unplug the tablet. When I unplugged the tablet, it completed screwed things up.  For some reason, I was not able to use the touch pad anymore (I could use it when the tablet was plugged in) and when scrolling up and down screens  it was very flashy and not a smooth transition.  I plugged the tablet back in, and alas...it wouldn't work.  It began to work like a touchpad (a very bad and hard to control one), which is how it worked before I set it up. I checked my xorg.conf file and found it to be exactly the same as before, so I tried restarting my comp, but that didn't work.  I ended up having to do ```
$ sudo dpkg-reconfigure -phigh x-server xorg 
``` in order to get my touchpad to work again. Does anybody know why this is happening, and if so how I could fix it?

---

