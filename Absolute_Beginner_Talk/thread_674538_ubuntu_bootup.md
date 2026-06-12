---
title: "ubuntu bootup"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by patnew2linux on 2008-01-21
Hey all, 

When i first got my ubuntu box from a friend it would boot right up into the desktop - but not i am having issues and since i am just getting started with ubuntu i thought i would ask for help

**1)  i get three options on bootup**
  a) ubuntu, kernel 2.6.20-15 generic
  b) safe mode 
  c) mem-test

**Problem #2 **
Frequence out of range error if i happen to bootup correcty...

PLEASE HELP looking to get this back on my network

---

### Post by Dngrsone on 2008-01-21
That is a typical grub menu.  Usually, you'll stick with the first.

The third option allows you to run memtest86+ if you suspect your memory may be bad.

The second (safe mode) is what you should boot for now until you can get your video problem resolved.

Frequency out of range means your video card is trying to send either a scan rate or refresh rate that is too fast for your monitor to handle.

When you boot into safe mode, you have to go to System, Preferences, Screen Resolution and change the preferred scan rate to something your monitor can handle (60Hz *should* work, no guarantees).

I am assuming that the hardware is all good.

---

### Post by frup on 2008-01-21
If the scan rate bit doesn't help, you may have a resolution that part of your hardware (gfx card/screen) doesn't really like.

With the grub there is a way you can make that stuff not visable. By default now on installs it waits 3 seconds where you can press esc I believe to view all the options... is yours waiting 20 seconds or so for you to choose and option?

---

