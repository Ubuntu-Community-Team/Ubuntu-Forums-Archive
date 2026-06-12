---
title: "not booting up"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by pgenette on 2007-01-25
Hello!

As a newbie to the ubuntu world, I'll attempt to be as descriptive as possible with my problem.  I'm running Ubuntu 6.06 on my Compaq Presario R3306US and had no problem until today when during the boot sequence stops responding on "starting system log". There is no Ok, no fail, and after a short while the GUI disappears and it goes into the console with "starting system log" still not responding.  After calling a friend who knows a little more then I do about the linux world, he told me to not boot on my latest kernel 2.6.15-27-386 and instead to load a previous version 2.6.15-23-386 (This did absolutely nothing). The next step was to boot in recovery mode and to load the Xorg.  This did not load up which my friend seems to believe means that there is a concern with loading the GUI.  I truly appreciate any assistance possible before wasting an excessive amount of time staring back at 0 with a fresh install.

---

### Post by Crakie on 2007-01-25
Does the LiveCD work?

How did you 'load' Xorg? Perhaps you mean X Server? How did you attempt to start it?

---

### Post by pgenette on 2007-01-25
Yes, I do mean X server, utilizing the command Xorg while booted in recovery mode(nothing loaded besides the mouse cursor in the shape of an X) . I had just written this to comment on the steps I have taken thusfar, do you have an suggestions for me???

---

### Post by Crakie on 2007-01-25
You should try typing: sudo /etc/init.d/xdm start where x=g if you use gnome, x=k if use kde or x=x if you use xfce. This will start X and your WM.

---

### Post by pgenette on 2007-01-26
Thank you Crakie, problem resolved :)

---

