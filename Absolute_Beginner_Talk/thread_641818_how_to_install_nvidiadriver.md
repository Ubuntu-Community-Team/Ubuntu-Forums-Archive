---
title: "how to install nvidiadriver"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by j_dog on 2007-12-15
For some reason my nvidia-gxl is broken. When I try to boot , the screen turns black. It boots into rescue and also from the live cd. When I try to remove nvidia-gxl, it says it is not installed. When I try to get it via apt-get , I cant access the repositories, it says error. I,ve been using Gutsy since beta.

Can someone help please ?

---

### Post by taurus on 2007-12-15
Shouldn't it be nvidia-**glx** or nvidia-glx-new?

Try removing either one from a recovery mode.

```
apt-get remove nvidia-glx
-or-
apt-get remove nvidia-glx-new
```
Then, you probably need to reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by j_dog on 2007-12-15
Thank you !   I will try it.

---

