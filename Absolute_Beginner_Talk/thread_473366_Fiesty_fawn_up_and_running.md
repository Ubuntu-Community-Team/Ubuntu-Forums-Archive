---
title: "Fiesty fawn up and running"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Deepak@CHN on 2007-06-14
Came back to Linux after a long time. Last time i installed was FC2 way back in 2004, had to come out as my system was too slow.

Upgraded my config and was searching for a nice distro. After some research and looking at this forum i made my mind on Ubuntu. Installation was very smooth.

Still have to install the latest nvidia drivers for my XFX 8600 GT. My broadband modem is having issues and was not able to connect to the net.

I did have the latest drivers but i did not not know how to stop the Xserver. When I tried 
```
 sudo ./ NVIDIA-Linux-x86-100.14.09-pkg1.run 
```
the installer came up but said i had to stop my xserver

have to try this 
```
sudo /etc/init.d/gdm stop
``` today evening and check if I am able to get the drivers installed.

Should i take any other precautions?

---

### Post by Inxsible on 2007-06-14
Congrats on a hassle free install.

---

