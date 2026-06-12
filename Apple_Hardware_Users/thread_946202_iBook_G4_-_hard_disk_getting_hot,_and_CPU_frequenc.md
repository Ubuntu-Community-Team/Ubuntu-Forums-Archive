---
title: "iBook G4 - hard disk getting hot, and CPU frequency scaling isn't working"
date: 2008-10-13
forum: Apple Hardware Users
---

### Post by Starlight on 2008-10-13
Hi! I have a problem... when I'm running Ubuntu on my iBook, the hard drive is getting rather hot. Is it dangerous? If yes, can it be fixed somehow? Another problem is that CPU frequency scaling doesn't seem to be working... the gnome applet shows that it's always running at full frequency (which is 1.2 GHz) even when I don't have any programs running, just the desktop. And I have no idea where to look for any frequency scaling settings.. can someone help me? :)

edit: I removed powernowd and installed cpudyn, because I've read somewhere that it can help, and it seems that it did... sometimes the processor speed drops to a half. :) But almost anything I do makes it go back to full speed again...

---

### Post by tiresia on 2008-10-15
> **Starlight said:**
>  And I have no idea where to look for any frequency scaling settings.. can someone help me? :)

edit: I removed powernowd and installed cpudyn, because I've read somewhere that it can help, and it seems that it did... sometimes the processor speed drops to a half. :) But almost anything I do makes it go back to full speed again...

If you want to know more about your system, you can have a look in /sys/devices/system/cpu/cpu0/cpufreq (/cpu0/ can be different according to your system).
There you will find your 'scaling available governors', the 'scaling available governor', as well as other important informations.

Anyway I would suggest you to go back to powernowd, because it keeps your system quiet (it works with the userspace governor).
 
You can reconfigure the gnome applets so that you can control the power of your laptop just choosing the right speed, when you need.
```
sudo dpkg-reconfigure gnome-applets
```
You can add to a panel the applet 'CPU Frequency Scaling Monitor' and control the Frequency as you prefer.

---

