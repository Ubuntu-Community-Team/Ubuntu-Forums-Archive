---
title: "Random Ubuntu problems (graphics and swap file)"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by cjv998 on 2007-12-12
Hi everyone, I've been having some random problems lately with 7.10 and Nvidia's restricted driver (I had Emerald installed, but removed it using sudo apt-get remove emerald, if that matters).

1. When my computer started up today, it scanned the hard drive since it hasn't been done recently, and I noticed it said it failed to mount/access/read the swap file (don't remember which term it used, but you get the idea).  I have been suspicious about whether or not the swap file was getting used correctly (Ubuntu seems to take longer than XP to load), and this confirms my suspicions I think.

 I also have several graphical/CCSM problems:

2. When I have the advanced desktop effects/Compiz Fusion enabled, sometimes my resolution will be incorrect on my desktop.  The pixel pitch is correct, but the desktop is simply too large, and I have to move the mouse to the edges of the screen to see the rest of it. (happens maybe 25-30% of the time, got so frustrating that I finally disabled Compiz Fusion altogether). --May be fixed, not sure yet.

3. I also noticed that my window borders were missing (just noticed it last night, but hadn't used Ubuntu in the last few days, was booting to XP) until I disabled Compiz Fusion.   I double checked, and I had the window decorations enabled, so that wasn't the problem.  --Never mind, hasn't happened again yet.

I must say, maybe it's because I'm not a computer pprogrammer and I'm not 100% comfortable with Ubuntu yet, but for hearing how stable it supposedly is, it sure seems to have a lot of weird problems for me.

So, any ideas how to fix these problems, and hopefully restore my confidence in Ubuntu?  Thanks!

---

### Post by pHreaksYcle on 2007-12-12
Just by taking a quick scan over your post, I have a possibility. Do you have a zoom feature enabled on Compiz? Also, is your resolution set correctly under System->Administration->Screen and Graphics?

---

### Post by cjv998 on 2007-12-12
Enhanced Zoom Desktop was enabled, so I disabled it, and we'll see if that helps.  My resolution was correct under Screens and graphics, but it looked like my refresh rate wasn't (it was set to 50Hz, and I'm pretty sure it should be 60, but that wasn't an option from the drop-down menu...I'll go double-check that now).  Never mind about the refresh rate issue, apparently there's a bug in X, where it doesn't display the correct refresh rate...so my monitor is actually running at 60Hz even though it displays 50Hz.

---

