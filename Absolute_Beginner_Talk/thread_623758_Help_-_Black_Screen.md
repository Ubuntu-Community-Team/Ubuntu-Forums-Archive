---
title: "Help - Black Screen"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by dive4d on 2007-11-26
1st post for a new user - I have been using Ubuntu 7.10 for a few weeks but the other day I went to change the screen resolution and this caused the screen to go black. I have not been able to use since then...

My machine is a dual boot system - graphics supplied by NVIDIA GeForce 3 Ti200 card. When I boot Ubuntu starts to load but before the login screen the NVIDIA logo fills the screen for a few seconds before the login screen (this never happened before). When I login the screen goes black - no keystrokes seem to do the trick.

Any help appreciated. :)

---

### Post by Digger78 on 2007-11-26
Boot into "recovery mode" and run

```
lspci
```

Note the numbers at the start of your graphics card line

i.e **01:01.0** VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

then run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dive4d on 2007-11-26
Digger78 - many thanks. Following your instructions seemed to do the trick - I am now back working in Ubuntu.

Cheers from a happy user :)

---

