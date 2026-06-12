---
title: "Text boot from installation CD -&gt; installed system?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Loranga on 2007-08-27
WHen I boot my computer from the installation CD, I can press F4 to boot in higher resolution than VGA. This combined with the removal of "quiet" and "splash" makes the computer boot screen like I want it. (text mode, verbose, high resolution).

How do I do this on an "installed" system?

(I have tried vga=ask, but  i get much less options (and with much lower resolutions) than I get from pressing F4 at boot CD startup. It feels as vga=ask just changes the amount of rows and columns and keeps the resolution at VGA)

I run Ubuntu 7.04 i386

---

### Post by kellemes on 2007-08-27
```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
```

I use vga=775 for 1280x1024

---

