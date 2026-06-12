---
title: "Which is the best if you have 2 kernels ?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by laruffii on 2008-03-18
I don't know how but after I update my ubuntu I got 4 choice menu added in GRUB , could somebody explain which one should I choose and the newest kernel only allow low video graphic settings and so slow at start up ???

---

### Post by NightwishFan on 2008-03-18
Generally the first one is the newest, the second is its "repair mode". The third is an older and the forth is its repair mode.

---

### Post by Rocket2DMn on 2008-03-18
Sounds like Ubuntu gave you an upgraded kernel.  What type of video card do you have and were you using restricted drivers before?
The top kernel should be the newer one which is preferable to use, assuming you can get it to work correctly.

---

### Post by laruffii on 2008-03-18
My laptop is acer 4520, and I upgraded atheros AR5700EG driver and also the nVidia 7000m driver from the nvidia'site for Unix driver , after installing real player my computer loose the sound, but I can finally get the sound again by executing the alsa1.sh script. but my graphic directly turn to be low, and startup was so slow

---

### Post by Rocket2DMn on 2008-03-18
I don't know about your sound problem, but with restricted drivers like nvidia's you need to reinstall them when you upgrade kernels.  If you're not down with that, you can just use your older kernel for now.  When you upgrade to Hardy, you might have to reinstall them unless the new version of X.org that they use detects it automatically.

---

