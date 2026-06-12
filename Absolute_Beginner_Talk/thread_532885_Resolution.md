---
title: "Resolution"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by jp316ad on 2007-08-23
Hey guys I have a problem that I've been trying to solve but nothing works. 

I am running from the Live Cd and want to install but when I get to the setup where it asks you for the region you are located at, I can't even scroll down to click next or whatever it says. I tried moving the window on top and tried moving it up alittle but its just too big.

I need to change the screen resolution and I typed in this code:

sudo dpkg-reconfigure -phigh xserver-xorg

but I get this:

xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20070823053639

What do I do now?

I also tried selecting a different resolution by entering F4 at the startup menu. But no luck. It selects it well but when it starts the resolution is back to 800 x 600. :confused:

---

### Post by Hobo Joe on 2007-08-23
What drivers are you using?

Paste the output of:
```

glxinfo

```

---

### Post by ridgeland on 2007-08-23
This is a redundant post see:
[http://ubuntuforums.org/showthread.php?t=532672](http://ubuntuforums.org/showthread.php?t=532672)
With the screen at 800x600 I don't see the [Forward] on the first install question unless I first shrink both the panels.
See the original post.

---

