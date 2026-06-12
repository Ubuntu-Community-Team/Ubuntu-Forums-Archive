---
title: "Lost my display resolution settings"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by oliverb on 2006-12-04
I recently switched monitors as the generic 17" crt I was using wore out. Unfortunately I'm now using an equally old Samsung Syncmaster 17GLi.

The problem I have is Ubuntu has gone into 640x480 resolution and I cannot select any other resolution, 640x480 at 60Hz is the only option available.

Please can someone tell me how to select a higher resolution.



Video: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

---

### Post by an.echte.trilingue on 2006-12-04
```
sudo dpkg-reconfigure xserver-xorg
```

will start a video configuration wizard of sorts.

Then restart your Xserver with CTRL+ALT+Backspace.

Good Luck
-mat

---

