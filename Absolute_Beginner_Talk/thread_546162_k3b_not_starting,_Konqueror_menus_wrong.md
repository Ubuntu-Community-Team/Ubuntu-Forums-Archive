---
title: "k3b not starting, Konqueror menus wrong"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by candtalan on 2007-09-08
7.04, (kubuntu)

k3b is not starting from its konqueror menus nor when I click the executable - it tries to start and the splash screen freezes, and the system monitor indicates k3b process is 'uninterruptable'. Following this I need to re- login or reboot, to clear the screen graphic.

Under some conditions, k3b does start however it declares it cannot find the CD writer at all, and the CDr drive does not react to its front button being pressed (to open it), it stays dead.

However, after a reboot, I can press the cd drive button, it opens, and I put in say, a (live cd for example) cd into the drive, then after a few seconds, the 'what action should happen?' window appears offering open cd, copy cd no action etc etc . When I choose copy cd, I get a *normal* k3b operating, and I can then choose use k3b normally.

thoughts - 
recently an unusual thing I did was to mount the floppy drive and use raw write to make a boot options  floppy diskette. I also noticed  that recently one of the update items did not seem to download at all. I think it was a K library of some sort. However, subsequently I checked for updates and they are reporting all is (now) up to date.

I also have 6.06 (kubuntu) on the same (multi boot) PC and this problem does not show itself. I note though, that I have not recently updated the 6.06 (last few weeks for example) if updates are a factor.

In addition to the non starting problem, at the same time, the konqueror Service menus for k3b seem to be screwed or at least changed, Now, when I right click onto an iso image file, I see the 'actions' does not include 'burn image with k3b' like it should (or as it used to, and as it still does in 6.06)

I uninstalled k3b and reinstalled, but nothing changed, fwiw.

Help appreciated  tia

---

### Post by sad_iq on 2007-09-08
Have you used --purge when you uninstalled??```
sudo apt-get remove --purge k3b
```

---

