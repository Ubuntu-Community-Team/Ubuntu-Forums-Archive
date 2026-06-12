---
title: "window bars disappear"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by spasmoid on 2007-10-28
I just upgraded to 7.10 and when I try the "extra" setting for visual effects, the window frame for every dialog box disapears. For instance, the menu bar is the edge of the top of the window with nothing above it.

consequently, you cannot do anything with the window - like move it, maximise it or whatever. There are no widgets because there is no bar for it to sit on.

I'm using the bog standard "nvidia" driver that is listed. The dialog detects it as the Geforce 6800 (generic). It is actually an nvidia GeForce 6600GT

---

### Post by auxilum on 2007-10-28
I had the same problem.  Try going to the Adv Desktop Effects Settings and enable 'Window Decoration'.

---

### Post by jandjfrench on 2007-10-28
Hi,

I have the same problem.  Where can I find "Adv Desktop Effects Settings"?

---

### Post by auxilum on 2007-10-28
System > Preferences > Adv Desktop Effects Settings

If you do not see it, then you may not have installed the:
'Compiz configuration settings manager' package

---

### Post by spasmoid on 2007-10-30
> **auxilum said:**
> I had the same problem.  Try going to the Adv Desktop Effects Settings and enable 'Window Decoration'.

installed it, tried it, makes no difference :(

---

### Post by ronald.higgins on 2007-10-30
Had the same issue, 

My memory could be wrong but it might have been libdecoration0 that i had to install .
If that fails just re-install compiz.

---

### Post by spasmoid on 2007-10-30
Yeah I tried apt-get install libdecoration0 and it said I already had the newest version

I removed compiz and then reinstalled it, no dice :(

---

### Post by amtnbiker16 on 2007-10-30
there have been lots of nvidia problems that are already covered in the forums.
i suggest you look around and get your drivers figured out and then go back and see if it works

---

### Post by sailor2001 on 2007-10-30
alt/f2  type: metacity --replace               also in your home hidden files (ctrl/h) look for gnomne 2 and remove the config script and then ctrl/alt backspace .. that will rewrite the config script

---

### Post by EXCiD3 on 2007-10-30
It could possibly be the default color depth for your graphics card.

Do a "sudo gedit /etc/X11/xorg.conf" in terminal, scroll down till you find the default color depth option (or search for it...it will be under your video card module) make sure taht default color depth is 24. This used to be a big problem with Compiz/Beryl in the past. This may not help whatsoever, just thought I would mention it in case.

Alt-F2 "metacity --replace" will use metacity as your window manager. Make sure emerald is installed (check synaptic) and you can do Alt-F2 "emerald --replace" to have window borders drawn using emerald instead of metacity.

---

### Post by cloudedice on 2007-10-30
I'm having a similar problem, but with a different cause.

By default "No Effects" is set, and I'm missing the window frames.  I can enable the "Extra Effects" and the window frames come back. However, on a reboot, or a reload of the session, the settings get reset to "No Effects"

Any ideas on how to make it permanent?

Thanks,
-ice

---

### Post by cloudedice on 2007-11-02
Any ideas on making it stick?

Thanks,
-ice

---

