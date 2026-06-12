---
title: "Missing files?? And screensaver trouble."
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by SunnyM on 2006-09-27
1st, I need to uninstall a few screensavers that came with ubuntu and cause my comp to crash, but don't know how to do it.

2nd, I read in a tutorial that gcursor and gnome-splashscreen-manager are in the repositories. But following the instuctions for installing (by following, I mean copy pasting the exact snippet) gets me an error saying they can't be found. ](*,) 

I think that's all for now, but I'm likely to have a lot more as I nose about the OS, lol.


Thanks in advance.:KS

---

### Post by charles.g.moore on 2006-09-27
did you enable the right repository for gcursor and gnome splash screen manager?

---

### Post by SunnyM on 2006-09-27
Maybe... *feels dumb* I used a tutorial.

[http://psychocats.net/ubuntu/sources]("http://psychocats.net/ubuntu/sources")

---

### Post by CatKiller on 2006-09-27
> **SunnyM said:**
> 1st, I need to uninstall a few screensavers that came with ubuntu and cause my comp to crash, but don't know how to do it.

Open Synaptic (System -> Administration -> Synaptic Package Manager) and uninstall the following packages, if they're installed:

rss-glx
xscreensaver-gl
xscreensaver-gl-extra

These are the screensaver packages that are most likely to cause a crash. If you happen to know which screensavers are causing the crash, then you could uninstall the package that has those in, and keep the others.

---

### Post by SunnyM on 2006-09-27
Well, I knew which ones, but they were from both. I didn't have the last one in there for some reason. Also, the repository did end up working, for some reason, even though I did the extra bit at the end of that tutorial and restarted, it still took a while to take affect.

---

