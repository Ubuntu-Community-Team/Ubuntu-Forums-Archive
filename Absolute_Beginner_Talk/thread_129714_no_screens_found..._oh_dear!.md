---
title: "no screens found... oh dear!"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by wrtpeeps on 2006-02-14
Hi, i recently installed ubuntu on vmware. However, when i tried to start it up, i get a 'fatal error: no screens found' when X tries to start. 

Anyone got any ideas how to fix this?

---

### Post by LordBug on 2006-02-14
You'll need to modify /etc/X11/xorg.conf and change it to the correct video/monitor setup that your VMWare session is using.

---

### Post by download17 on 2006-10-13
Hey... I have  almost the same problem.  I'm running and AMD64 3200+, Sapphire x800gto etc... When I try to boot off of the Live Cd I get the whole "no screens found" and "(EE) Devices not found" just above it and then it goes to a prompt. I've been searching these forums and have found lots .  This is what I've done so far:

-sudo dpkg-reconfigure xserver-xorg
(and then I went through all the reconfiguring of xserver
-startx
(this doesn't work)
-sudo gedit /etc/X11/xorg.conf
(This doesn't work... so I can't edit the xorg.conf file... neither nano or vi or any other method of editing files works... if I use nano it says that I've opened a new file.  There's something fishy going on...)

Pleas Help!!!
Luke D.

---

