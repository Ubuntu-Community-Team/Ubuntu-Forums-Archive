---
title: "Video card problem with 7.04 install"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by DrPppr242 on 2007-04-20
alright so I've been running edgy eft on my laptop for a couple months now and love it but everytime I've tried to install any version of ubuntu on my desktop I've had the same problem.  It recognizes the live CD and starts to boot like normal (the cd is fine I tried it on another computer) and te Ubuntu logo shows up while it loads, I hit alt f1 and everything loaded fine except the wireless drivers but when I here the music like gnome is loading both my monitors disapear and say out of scan range like they're not plugged into a video card. I have a nvidia 6800GT and everything works fine under Sabayon linux so the problem has to be with my video card not working with Ubuntu, and I think I could just activate under the restricted drivers, but because I have no monitors I don't know how to go about trouble shooting this problem, any help would be great.

-paul

---

### Post by lamalex on 2007-04-20
it seems to be detected your refresh rate wrong, can you get to a terminal? after you hear the music hit control alt f1 and do a ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` if it fails, try doing it without phigh.

---

