---
title: "nVIDIA 6600GT Help"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by NanoXbuG on 2007-01-27
Here's the rub...

I have no idea where to begin when it come sto getting Ubuntu to support my video card (nVIDIA 6600GT)

I am at a complete loss!!!

Any help is greatly appreciated!!!

---

### Post by Koybe on 2007-01-27
This should do the trick :
```
sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
```Then either restart Xserver or reboot your PC.

Good luck.

You can also you this after installation if you want :
```
sudo nvidia-xconfig
```

Before doing all this, you can also make a backup of your actual config file... just in case.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```

---

### Post by NanoXbuG on 2007-01-27
I actually just used automatix2 for 6.06

It worked like a charm

Thank you no less!

---

