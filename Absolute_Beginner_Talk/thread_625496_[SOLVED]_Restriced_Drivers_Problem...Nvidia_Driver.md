---
title: "[SOLVED] Restriced Drivers Problem...Nvidia Driver"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Soilworker on 2007-11-28
Yeah I'm new to linux and I'm trying to get my Nvidia drivers to install however when i go to the Restriced Drivers application and I try to enable the device/driver I get a message saying "The software source for the package nvidia-glx-new is not enabled". In addition if I try to install the drivers using the terminal and shutting down the X server (using "sudo /etc/init.d/gdm stop") i go to a black screen where i can type. But before i can type much i get a message saying:

"[ 821.768147] bcm43xx: Error: Microcode "bsm43x_microcode5.fw" not available or load failed"

Thanks.

---

### Post by PmDematagoda on 2007-11-28
Post the results of:-

```
cat /etc/apt/sources.list
```

---

### Post by MozartlovesUbun2 on 2007-11-28
you could also try ENVY
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

read about it first carefully how to install and use
it will give you the latest drivers

---

### Post by Soilworker on 2007-11-28
Yeah so I figured out my problem...I had to manually download the driver and firmware for my wireless card and from there I allowed restricted drivers to be downloaded and that fixed my problem.

---

