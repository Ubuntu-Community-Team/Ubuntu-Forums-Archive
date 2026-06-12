---
title: "[SOLVED] Screen Resolution problem on MacBook"
date: 2008-06-05
forum: Apple Hardware Users
---

### Post by PaulFXH on 2008-06-05
I have a number of Linux OSes on my MacBook (C2D, 2.16 GHz, 2007) (Ubuntu Hardy, Sidux 2008-1 and Foresight Linux 2.0.2)
In Ubuntu and Sidux, the screen resolution is 1280x800 without me having done anything special even though no Modeline is present in the xorg.conf file in either distro.
However, in Foresight I can get no higher than 1024x768.
(OK, I know this is a Ubuntu forum, but Foresight is a relatively new, but very cool, distro with a forum that is very much less active than this one right now).
I have tried both the i810 and the intel drivers (in /etc/X11/xorg.conf) but neither gave any higher resolution than 1024x768.
I have also included 
```
Modes  "1280x800"
```
in the Display subsection of xorg.conf in Foresight, but this line seems to get overwritten, or lost, on restarting X.
I've been messing around with this for a couple of days without making any progress.
I should mention that I have the same version of Foresight on my Desktop where I can get 1280x1024 screen res without any modelines in the Display subsection of xorg.conf.
Anybody got any ideas what else I might try?

---

### Post by Keeters on 2008-06-06
You might try using the 915resolution package. It works for the following chipsets: 845G, 855G, 915G, 915GM, and 945G. I don't know much about Sidux except that its debian based so that package should be in the repository somewhere. I've had to use it every time I want 1280x1024 on my macbook.
Good Luck

---

### Post by PaulFXH on 2008-06-07
Thanks for the reply.
915resolution was actually installed and the problem was with Foresight rather than Sidux.
Nevertheless, it seems I didn't actually have a problem at all. It's just that when I checked in System>>Admin>>Display (equivalent to System>Preferences>Screen Resolution in Ubuntu) the screen resolution was shown as 1024x768.
However, /var/log/Xorg.0.log clearly shows that the 1280x800 resolution is activated during the boot.
Another Foresight user told me that he has the same error.
So it seems this is a Foresight bug.:)

---

