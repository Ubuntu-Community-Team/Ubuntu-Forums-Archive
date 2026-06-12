---
title: "Display dithering"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by cakewalker on 2008-01-10
I'm running Ubuntu 7.10 on a fairly new Sony laptop (VGN-N31S - one of their cheapest). Installing 7.04 wasn't a problem and the upgrade to 7.10 went without a hitch. Compared to the rediculously involved Windows XP install for this machine, Ubuntu went remarkably smoothly. The only two problems I've had were trying to work out how to turn the speakers off (solved) and an issue to do with dithering of colours on the screen. The GIMP, Firefox and the image viewer all show images I have with subtle gradiations of light grey with very obvious dithering. Windows on the same machines doesn't seem to have the same problem. I've tried upping the colour depth in Ubuntu only to find it's already at its maximum. Perhaps I'm using the wrong search terms but a search for dithering didn't seem to turn up anyone else having the same problem. Any ideas would be very gratefully received!

Incidentally, it's an Intel 945 i810 Integrated Graphics Chipset.

Thanks!

---

### Post by nikoPSK on 2008-01-11
you could try reconfiguring xorg:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

