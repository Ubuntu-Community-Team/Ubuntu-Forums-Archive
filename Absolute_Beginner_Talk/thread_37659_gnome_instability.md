---
title: "gnome instability"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by asarwate on 2005-05-28
I seem to have something buggy with gnome.  Every time I log in, it complains of gnome-panel exiting unexpectedly, or some sub-applet of gnome-panel exiting unexpectedly.  Once even nautilus exited unexpectedly.

I tried reinstalling gnome-panel using

sudo apt-get install --reinstall gnome-panel

but that didn't seem to help at all.  I'm not sure what to do to fix this -- at the moment it's more of an annoyance, although occasionally firefox will crash and take gnome-panel with it or will freeze, necessitating a reboot (and hence a fsck, etc etc etc).

Any thoughts welcome.

---

### Post by TravisNewman on 2005-05-28
what panel applets do you have running? It could be a problem there. Do you have bubblemon? That one has caused problems for a lot of people.

---

### Post by asarwate on 2005-05-28
I haven't installed any new applets, so it's just stuff like the update notification applet, the sound monitor, the clock, etc.

I had a bit of a hard time installing in the first place (the cd files copied to the hard drive for the second part were buggy and I ended up doing a net-install), so I might need to... recompile the kernel or something.

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=asarwate]
I had a bit of a hard time installing in the first place (the cd files copied to the hard drive for the second part were buggy and I ended up doing a net-install), so I might need to... recompile the kernel or something.[/QUOTE]

nothing that drastic is needed I bet. Are you using the PPC version by any chance?

---

### Post by asarwate on 2005-05-28
No, this is plain old x86 version running on an AMD processor.

Should I try reinstalling gnome wholesale?  I'm just afraid of losing Xwindows or whatever and getting booted back to the console permanently.

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=asarwate]
Should I try reinstalling gnome wholesale?  I'm just afraid of losing Xwindows or whatever and getting booted back to the console permanently.[/QUOTE]

No. try uninstalling gnome, then reistalling it.

---

### Post by asarwate on 2005-05-28
Will do -- I'll let you know what happens.  Thanks!

---

### Post by asarwate on 2005-05-30
That seems to have fixed it -- thanks!

---

### Post by poofyhairguy on 2005-05-30
[QUOTE=asarwate]That seems to have fixed it -- thanks![/QUOTE]

no problem.

---

