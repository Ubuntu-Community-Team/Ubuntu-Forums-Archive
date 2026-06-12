---
title: "Nvidia: External Monitor garbled on Macbook Pro 5,4 with Karmic Koala 9.10"
date: 2009-11-30
forum: Apple Hardware Users
---

### Post by phorque on 2009-11-30
Have had a surprisingly successful time getting Ubuntu up and running on this machine apart from this one issue (See attached photo). I have tried Xinerama and TwinView. 

I think the problem might be Compiz, but maybe there's a way around it? Can anyone point me to a thread that might help me troubleshoot this problem? The model of monitor is HSD Hanns.G Hi221 and the Nvidia card is the GeForce 9400M. Using Nvidia driver version 185.

---

### Post by linuxopjemac on 2009-11-30
what about this thread, did you try it?:

[http://ubuntuforums.org/showthread.php?t=1327758&highlight=external+monitor](http://ubuntuforums.org/showthread.php?t=1327758&highlight=external+monitor)

---

### Post by phorque on 2009-12-01
I was on the 185 drivers, but the 190 drivers were what I needed:

1) Add this repository
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) 

2) install the 190 drivers with ...
```
sudo apt-get update
sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190
```

2) Go to System > Administration > Hardware Drivers and disable your old nvidia drivers. reboot.

3) Go back into Hardware drivers and enable the 190 drivers, reboot again.

4) Twinview should now work!

---

