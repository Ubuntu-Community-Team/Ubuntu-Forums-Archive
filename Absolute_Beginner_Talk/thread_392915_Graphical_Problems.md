---
title: "Graphical Problems"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by MustangGT on 2007-03-25
Alright so I've install Ubuntu.  Graphics during initial load work fine.  Now I start Ubuntu and it gets past the the "Ubuntu" screen where it loads everything.

Takes me to the standard shell prompt, after a few seconds it launches a window, blue with a box in the middle - "GDM shut down because it's not properly configured" or something like that.  So I went and killed the GDM process, tried to restart it, failed, same issue.  Viewed the log it generated, it said "No Screens Found".

Not sure what that is about, it detected both my onboard video (disabled) and my Geforce FX 5500 Card.  Well, actually the Nvidia card was detected as "Unknown Nvidia".  It's connected to a dell flatscreen monitor.

Anyone know the problem?

Thanks much,
Louis

---

### Post by r4ik on 2007-03-25
Try in a Terminal,

sudo dpkg-reconfigure xserver-xorg

Follow the defaults and set you're graphics to nv
If you have a visual you could try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

