---
title: "[SOLVED] Virtual Concrete"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by ByKeLaO on 2007-12-15
Hi there,
I'm trying to set up a Vista+Ubuntu dual boot. I got the feisty live CD and tested it out, and it runs perfectly. Everything seems to be in order. So I tried to install it.

The first problem I had was that after a fully automatic install, it wouldn't boot. It complained about a "missing operating system". After restoring my MBR, I decided to do a manual install and now it is working. Almost.

It's incredibly slow. It takes about 10 mins to get to the login screen, and then it runs at about 1 frame every 5 seconds. As you can imagine, it is completely unusable.

What's the problem and how do I fix it?

Hardware
---------
Asus commando motherboard
Intel Celeron D 2.7GHz processor (soon to be replaced with core2 duo)
2GB DDR2 RAM
320GB SATA HDD (on which linux and windows are both installed)
80GB IDE HDD
ASUS EN7600GT Graphics card

Any help will be gratefully received!

---

### Post by overdrank on 2007-12-15
> **robinjam said:**
> Hi there,
I'm trying to set up a Vista+Ubuntu dual boot. I got the feisty live CD and tested it out, and it runs perfectly. Everything seems to be in order. So I tried to install it.

The first problem I had was that after a fully automatic install, it wouldn't boot. It complained about a "missing operating system". After restoring my MBR, I decided to do a manual install and now it is working. Almost.

It's incredibly slow. It takes about 10 mins to get to the login screen, and then it runs at about 1 frame every 5 seconds. As you can imagine, it is completely unusable.

What's the problem and how do I fix it?

Hardware
---------
Asus commando motherboard
Intel Celeron D 2.7GHz processor (soon to be replaced with core2 duo)
2GB DDR2 RAM
320GB SATA HDD (on which linux and windows are both installed)
80GB IDE HDD
ASUS EN7600GT Graphics card

Any help will be gratefully received!

Hi, have you installed the graphics driver for the nvidia card through restricted manager? You may also look a Envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ubutufan on 2007-12-15
When using the livecd was the performance similar?

---

### Post by ByKeLaO on 2007-12-15
> **overdrank said:**
> Hi, have you installed the graphics driver for the nvidia card through restricted manager? You may also look a Envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
When using the LiveCD it ran perfectly well. It was just after installing that the performance went downhill.
No, I haven't been able to install the nVidia driver because I haven't yet managed to set up internet on Ubuntu (because I can't even log in due to its slowness).
Any other ideas?

---

### Post by ByKeLaO on 2007-12-15
Should I install an old version of ubuntu and see if it works better?

---

### Post by ByKeLaO on 2007-12-15
bump

---

### Post by forestpixie on 2007-12-15
you could try booting to recovery - when you get to the prompt try this command to configure your card - if you know the answers give them, if not go for default - you can always have another go. Try using the right video driver - but if necessary go for vesa

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hope that helps

---

### Post by ByKeLaO on 2007-12-15
Hi,
I just tried your suggestion, but the list of drivers does not include "NVIDIA" on my PC. It lists every type of card except for mine. Help please!

---

### Post by forestpixie on 2007-12-15
I would use vesa then as the driver - it should get you going, then once you're up use restricted driver manager in admin >system to get the right driver - if you can't get the right driver through that try using envy - but you need to be able to get it going first

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ByKeLaO on 2007-12-15
I just realized there is a new version of Ubuntu out now. I'm going to try installing that instead (since feisty doesn't seem to work). Please lock this thread, I will start a new one once 7.10 is installed.

---

### Post by forestpixie on 2007-12-16
just mark it as solved

---

