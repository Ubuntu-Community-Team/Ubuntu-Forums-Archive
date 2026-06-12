---
title: "SLI successful?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-29
Has anybody successfully gotten SLI to work with 2 video cards?

I've done all the steps to enable it that i can find at nvidias documents addng "SLI" "1" or "SLI" "AFR" to my xorg.conf

but running glxgears still shows on average 8000 fps with sli on and off.... and i cant turn on dynamic shadows in games without completely chugging out my system, And my system isnt one to normall chug on windows at least... dual 6800XT video cards, 2 gigs of ddr400 memory. amd64 3000+

anyways i cant figure out any other way to get SLI turned on or get confirmation that it is actually on and just malfunctioning any help would be appreciated.

---

### Post by Jeroen Vernooij on 2006-05-29
I don't know for sure if this is needed, but have you restarted X (ctrl alt backspace) after making the change to xorg.conf?

---

### Post by NobodySpecial on 2006-06-14
Answer from [http://www.phoronix.com/scan.php?page=article&item=326&num=5]("http://www.phoronix.com/scan.php?page=article&item=326&num=5"):

"After enabling any SLI mode and then restarting Xorg, the screen will look much the same as previously in a single-card setup along with nvidia-settings, however, there are a few finer points worth mentioning. First off, with nvidia-settings under the graphics card information page, the Bus Type will display the PCI Express speeds for the SLI setup which will be x8 unless using the newer nForce4 X16 Chipset. Next up, under the OpenGL settings page, under miscellaneous the check-box item of Enable SLI Heads-Up-Display. As of yet NVIDIA hasn't implemented any dedicated SLI utility or created any game/application profiles for better benefiting the frame-rate performance of the various OpenGL programs."

So in summary, type in Terminal:
```
nvidia-settings
```
and look for something like "PCI Express 8x" under the first screen, then click "Open GL Settings" and look for "Enable SLI Heads-Up-Display".

---

### Post by thexaspect on 2006-10-10
and dont forget to backup everything, because i just lost my whole config when it didn't work as advertised......

---

