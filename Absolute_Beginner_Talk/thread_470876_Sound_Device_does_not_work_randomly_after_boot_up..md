---
title: "Sound Device does not work randomly after boot up."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Najand on 2007-06-11
Well, I have an NEC Lavie G computer and I have an annoying problem. The Sound Device (according to /proc/asound) are ATI IXP (alsa mixer), ATI IXP Modem(alsa mixer) and Analog Device AD1981B(OSS Mixer). Well, the one that works is ATI IXP(alsa mixer). However it sometimes does not load during boot up and I can just see ATI IXP Modem Device (It loads all the time). I don't know how to solve this problem and in case if it is a bug I don't know how to report that... Any help is appreciated. Thanks in advance for your help.

---

### Post by ryanVickers on 2007-06-12
I've had this happen to me before too, it seams fairly random, except for if you change the login/off/ready sounds, sometimes this will do it.  I've found just disable the sounds (mostly the logon screen ready one), switch the sound device (volume control) and reboot.  This should fix it?! ;)

---

