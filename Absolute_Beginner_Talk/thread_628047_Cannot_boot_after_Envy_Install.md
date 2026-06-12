---
title: "Cannot boot after Envy Install"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Knuxyl on 2007-11-30
I have a geforce nvidia 8500gt graphics card and the resolution was set to 1280x1024. i remembered before i couldnt set up the best appearance settings because when i would restart i would get a screen, it would talk about the kernel crap and then just go to a black screen (my monitor would lose signal). i went and instead envy cuz i saw it downloaded from the nvidia website. i installed it, chose install nvidia drivers, when through all that, and then it said to restart. i did and now its doing the exact same thing, no monitor signal. what can i do to fix it? im a total newb at linux. thank you

---

### Post by Knuxyl on 2007-11-30
**bump**

---

### Post by PmDematagoda on 2007-11-30
Try:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Knuxyl on 2007-12-01
i cant even boot up though, how do i get to a text interface?

---

### Post by PmDematagoda on 2007-12-01
Did you try booting Ubuntu through Recovery Mode?

---

### Post by Majorix on 2007-12-01
I am an anti-Envyist. It only caused me trouble, so on my desktop with an ATI card I use the open source "radeon" drivers and on my laptop with Intel card I use "i810". I have 3D rendering on both and I can use Compiz Fusion to its full extent too. No need for proprietary drivers, let alone a buggy script that tries to install them for you and screws your system up.

As suggested, boot into recovery mode and do a
```
dpkg-reconfigure xserver-xorg
```

---

