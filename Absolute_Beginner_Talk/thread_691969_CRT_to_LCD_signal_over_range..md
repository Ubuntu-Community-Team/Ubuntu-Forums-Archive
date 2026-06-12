---
title: "CRT to LCD signal over range."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by confused! on 2008-02-09
Hey,
was using 21" CRT, dropped resolution to 1024x768 and plugged in a 15" LCD instead. However, the display is working, it just has a big red box dancing all over it saying signal over range. Guessing I need to drop the refresh rate, though can't work out how to go any lower than I am! Any ideas?

---

### Post by overdrank on 2008-02-09
> **confused! said:**
> Hey,
was using 21" CRT, dropped resolution to 1024x768 and plugged in a 15" LCD instead. However, the display is working, it just has a big red box dancing all over it saying signal over range. Guessing I need to drop the refresh rate, though can't work out how to go any lower than I am! Any ideas?

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by confused! on 2008-02-09
When I tried it I got to a colourful (largely blues and grey) screen and followed steps as i thought i should but problem appears to persist. May just stick to my CRT sun tan box. Looking a little pale. Thanks for the help though!

---

