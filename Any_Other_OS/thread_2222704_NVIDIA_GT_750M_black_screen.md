---
title: "NVIDIA GT 750M black screen"
date: 2014-05-07
forum: Any Other OS
---

### Post by jacob36 on 2014-05-07
I've been attempting to resolve this issue for days, with no success. I'm fairly new to linux. I don't know anything about reinstalling the kernel (Although it sounds easy from what I've read). The window manager I'm currently using is KDE. I installed the nvidia drivers with pacman -S nvidia, then tried using startx. The screen goes black and my GPU fan comes on at full speed, then the laptop reboots after a few seconds. I also tried installing the proprietary drivers from NVIDIA's website with the same results. I've tried using nvidia-xconfig and bumblebee. The Xorg.0 log file has the entry ```
Screens found, but none have a valid configuration
``` or something similar to that.

I would have posted this on the Arch Linux forum but the verification is seemingly impossible in my state.

---

### Post by oldfred on 2014-05-07
do not know about pacman and what version nVidia driver you are getting but you need a new one as your card is very new.

              
 [http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

I gather the 750m is not the new 750 cards just released?

I do know that you cannot easily install another nVidia drive after installing one. You must purge all nvidia and settings in system before downloading and installing another driver. You get conflicts otherwise.

---

