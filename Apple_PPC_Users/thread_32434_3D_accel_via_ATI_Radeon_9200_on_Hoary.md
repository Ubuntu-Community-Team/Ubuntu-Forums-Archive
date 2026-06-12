---
title: "3D accel via ATI Radeon 9200 on Hoary"
date: 2005-05-07
forum: Apple PPC Users
---

### Post by a monkey on 2005-05-07
Sorry for posting pretty much the same thing twice, but I didn't seem to get any answers when I posted it in the Hardware forum. I thought maybe posting to forum that focuses directly on Apple machines might get me some more answers.

I asked how to get 3D acceleration via my ATI Radeon 9200 video card, and was told to use the "opensource" drivers. Does anybody know where to get those?

---

### Post by khc on 2005-05-07
It's included. In your /etc/X11/xorg.conf, replace
Driver          "ati"
with
Driver          "radeon"

---

### Post by a monkey on 2005-05-08
Thanks a bunch!

---

