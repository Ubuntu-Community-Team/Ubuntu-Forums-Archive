---
title: "Display is all screwed up! Showing random vertical lines"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-13
I tried posting something similar in the hardware help, but this forum has been more beneficial to me in the past.

I just installed an XFX GEFORCE 6800 (NVIDIA) video card.  I rebooted my computer, everything was showing up normal.  Bios came right up, Grub displayed my options, and then the boot splash screen that shows you all the stuff thats being initialized was working as well.  Once it got into the actual Session Manager (I think thats what its called, the part that asks you for your login credentials) everything got mangled.  I just see vertical lines of nonsense.

I logged in for the hell of it even thoguh i couldnt actually see the prompt.  I heard the normal initialiation sounds and then i assume i was at the desktop, but it was unrecognizable.  Any idea what the problem is?

i tried going into recovery mode and doing apt-get install nvidia-aglx.  Everything downloaded and was installed, but when i booted up normally it still gave me the garbage at the session manager..

Any ideas on what's causing the problem?  Am i not using the right drivers?  If not, which should i use, how should i get them since i cant get into my desktop?


Thanks.

---

### Post by bodhi.zazen on 2006-09-13
Try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Rizla on 2006-09-13
> **bodhi.zazen said:**
> Try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will do, once i get home later tonight.  Thanks.  I need all the help i can get.

---

