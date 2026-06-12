---
title: "No xgl after kernel update"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-07-27
So I recompiled the 2.6.17.7 kernel form kernel.org
But everytime I boot up I have to manually do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
but my xgl doesnt work.
So I edit the xorg.conf but when I try to restart X the console tells me that there is no screen found.
so I ( again ) have to do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Can someone help me ?

---

### Post by PingunZ on 2006-07-27
nobody ?

---

### Post by atrus123 on 2006-07-27
reinstall your video driver.

---

### Post by mcduck on 2006-07-28
You also need restricted modules etc. for your new kernel, otherwise youre graphics cards drivers won't work and you'll loose 3D acceleration (and thus XGL/Compiz too..).

---

