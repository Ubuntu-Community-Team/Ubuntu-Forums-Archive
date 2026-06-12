---
title: "Arch Linux: After reboot nothing works."
date: 2008-08-04
forum: Arch and derivatives
---

### Post by squidmaster on 2008-08-04
OK so I've reinstalled Arch 4 different times with 4 (flux, open, XFCE & LXDE) different DE's (technically 3, LXDE and openbox are the same...)
and every time after I restart I don't have network or any network commands working (IFconfig, iwconfig ect) as well as a bunch of other commands (halt, hwdetect, and quite a few more)....

sometimes after two or three restarts (I end up just using "sudo /sbin/halt") all my menus discontinue working and I can't get any control over anything.

Not only does my wireless stop working my wired internet stops as well.

Anyway I'm not new to linux, but new to the newer versions of arch (I used it a few years back but it's a bit different now) and I really just want to get everything working and keep them working because this is getting quite annoying not having any network connection.....

The first reboot after I finish the install from CD everything works FINE
then I reboot it one more time and nothing works then....

Also, I guess a lot of stuff DOES work (X, XFCE, ect) BUT the things I really NEED don't work.

---

### Post by squidmaster on 2008-08-04
also if I do a pacman -A _____ (wireless_tools or madwifi or what ever) and select the packages from the disk it says they are already installed.... go figure?

---

### Post by K.Mandla on 2008-08-04
Shifted to Arch Linux forum.

---

### Post by cardinals_fan on 2008-08-04
I noticed this once.  Are you SURE that you checked the wireless_tools package during package selection?

---

### Post by jrd on 2008-08-06
I dont use wireless so I'm not sure but...make sure you have all the needed modules and daemons in rc.conf. Sounds like this may be the problem since it only messes up after reboot.

---

### Post by K.Mandla on 2008-08-06
> **cardinals_fan said:**
> Are you SURE that you checked the wireless_tools package during package selection?
I did that once too. I wondered why none of the iw commands worked, and it was because I hadn't ever ticked the wireless tools package. :roll:

---

