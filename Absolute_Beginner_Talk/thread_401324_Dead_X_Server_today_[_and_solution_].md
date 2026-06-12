---
title: "Dead X Server today [ and solution ]"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by thewump on 2007-04-04
I have no idea what is going on here, but today I did a reboot and everything went to hell.  I thought I'd document it in case it happens with others.. I think it must be something to do with an update I allowed yesterday, but isn't evident until a reboot.

I'm running 6.10 with Beryl, on an NVIDIA card using the envy installer from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I rebooted and after login to gnome, kde, safe gnome etc. I just got a flash then back to login.  

The tail of the log /var/log/Xorg.0.log showed:

AUDIT: Wed Apr  4 11:23:54 2007: 6366 X: client 2 rejected from local host

A google of that brought up a couple of threads about libglx.so and when I looked at that file in:

/usr/lib/xorg/modules/extensions/

I found that it was a file ( not a symbolic link ) with a date of yesterday afternoon.

Ahah..

I used ENVY ( see link above to the site of the guy who I would love to buy a beer for ) to reinstall the drivers.. It noted that the symbolic link was lost, and recreated things correctly.

Note.. I had to run envy from an SSH session from another machine.. It blanked out for some reason when I ran it in failsafe terminal.

---

