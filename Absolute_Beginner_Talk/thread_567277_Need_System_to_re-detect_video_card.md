---
title: "Need System to re-detect video card"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by chris walters on 2007-10-04
I did this before but I can't remember how. My system incorrectly believes that I only have 640x480 vga resolution when I have at least 1024x768 svga. How to I start video card re-detection on Ubuntu 6.06 LTS. Thank you very much for your help.
Chris

---

### Post by ThrobbingBrain66 on 2007-10-04
```
sudo dpkg-reconfigure xserver-xorg
```
Just accept the defaults for questions you aren't sure about.

---

