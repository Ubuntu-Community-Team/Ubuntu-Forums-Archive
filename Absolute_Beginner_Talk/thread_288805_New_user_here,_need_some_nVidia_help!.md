---
title: "New user here, need some nVidia help!"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by pscl227 on 2006-10-30
Right, well i'm a brand spanking new user to linux and ubuntu, so be gentle! 

Built a machine from spare ods and sods i have around to try out ubuntu on, xp2200+. 512MB ram, 80GB hd, nVidia FX 5800ultra, i've installed ubuntu then i did

> sudo apt-get install nvidia-glx

to install the nvidia drivers, i then set it up so i could change the settings from my desktop accoring the the guide on this site.

now when i boot my monitor says "out of range" so i presume it is at too high a resolution, so how do i change my desktop resolution from terminal??

thanks, Paul

---

### Post by Iarwain ben-adar on 2006-10-30
Hi,
just type in this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should ask you some questions, under wich the resolution you would like.


Iarwain

---

### Post by GIFRATE on 2006-10-30
If you haven't done it yet, you can try this to configure automatically xorg.conf

```
sudo nvidia-xconfig
```

---

### Post by mips on 2006-10-30
Just follow this thread and get the drivers/guide below.

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

