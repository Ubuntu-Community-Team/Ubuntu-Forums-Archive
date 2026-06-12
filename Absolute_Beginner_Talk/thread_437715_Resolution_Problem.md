---
title: "Resolution Problem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by MrMatt2532 on 2007-05-09
I am running Ubuntu 7.04 on an asus w3v laptop. It has an ATI X600 mobility.  I don't have the restricted drivers enabled because my system freezes up periodically when using these. For my screen, the optimal resolution is 1280x768 (widescreen), but i am forced to use 1024x768.  1280x768 shows up as an option on the screen resolution preference, but when i select it the screen has all sorts of problems. The middle of the screen looks fine, but 2 inch columns on the right and left flicker and look scrambled so i am forced to go back. Am i just out of luck or does anybody have suggestions to get this resolution working?

---

### Post by uclalinux on 2007-05-09
Run:

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by alienexplorers on 2007-05-09
Are you using a CRT or LCD screen?  What refresh rate are you trying to run?

---

### Post by 63holden on 2007-05-09
thanks for the tip uclalinux , I had the same problem but once I ran the reconfigure and added the resolution I wanted 1280x800 ( even though it was shown as a choice on the screen resolution menu before hand) I selected 1280x800 again and it worked with no distortion :)

---

### Post by MrMatt2532 on 2007-05-09
I tried running "sudo dpkg-reconfigure -phigh xserver-xorg", i'm guessing i was just supposed to choose ATI and my desired resolution? Update: doing this didn't seem to do anything...should i be choosing something else?

> **alienexplorers said:**
> Are you using a CRT or LCD screen?  What refresh rate are you trying to run?

LCD screen, i would like to use 85Hz because i know that should work, but only 60 Hz shows up. But first and foremost i want the correct resolution.

---

### Post by alienexplorers on 2007-05-09
Try adding a modeline to you monitor section of xorg.conf...  A modeline generator is at [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) ...  A mode line for 1280x768x85 would be like so:

>   # 1280x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 118.53 MHz
  Modeline "1280x768_85.00"  118.53  1280 1368 1504 1728  768 769 772 807  -HSync +Vsync 

---

### Post by MrMatt2532 on 2007-05-09
> **alienexplorers said:**
> Try adding a modeline to you monitor section of xorg.conf...  A modeline generator is at [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) ...  A mode line for 1280x768x85 would be like so:

Wow, seems to have fixed it. I am a little confused though, where i select the screen resolution, it shows the correct resolution but still says the refresh rate is 60Hz. What does this mean?

---

### Post by alienexplorers on 2007-05-09
It could mean the refresh rate is too high.  Try 70hz as the refresh rate.

>   # 1280x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 94.98 MHz
  Modeline "1280x768_70.00"  94.98  1280 1352 1488 1696  768 769 772 800  -HSync +Vsync

---

### Post by MrMatt2532 on 2007-05-09
> **alienexplorers said:**
> It could mean the refresh rate is too high.  Try 70hz as the refresh rate.

Ok i tried that. Same thing, it just says 60Hz. Could it actually be at a higher refresh rate, and it is just displayed wrong?

---

### Post by alienexplorers on 2007-05-09
That's possible.  My Nvidia car is running at 75hz and the screen resolution shows that I am running at 55hz.  Sounds odd, but it happens.  As long as the screen is not flickering then I would not worry about it.

---

