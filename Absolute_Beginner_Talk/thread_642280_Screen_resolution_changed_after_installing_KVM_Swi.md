---
title: "Screen resolution changed after installing KVM Switch"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by ProcessOp on 2007-12-16
I just recently installed Ubuntu 6.04 on my antiquated machine (Athlon 2000+, ATI R-100 Video card) and  it installed beautifully with the correct resolution for my monitor, but now my only choices are 600 x 400 or 800 x 600.

any help would be appreciated

---

### Post by spydon on 2007-12-16
```
dpkg-reconfigure xserver-xorg
```

Try that one it might help.

---

### Post by blackbelt_jones on 2007-12-16
> **spydon said:**
> ```
dpkg-reconfigure xserver-xorg
```

Try that one it might help.

I just logged in looking for help with the same problem (different cause), and it worked for me... plus,  as an added bonus, I learned how to disable my Caps Lock key!  (Caps Lock is a fine idea for a key, but a terrible location, right next to the A where I am always hitting it with my pinkie.)

I've heard of these configurations being lost on reboot, so I backed up the /etc/X11/xorg.conf file just in case.

Also, I should note that when I first tried to restart x, it didn't work.  It looked like I might have broken X, but then reran the nvidia-xconf untility from the nvidia driver download page, and that got me running again, with the enhanced resolution options  I had sought.  It sucks having a 22 inch lcd screen and being stuck with 800x600 resolution... 1024x768 is a huge improvement, :KS  Thanks!

---

