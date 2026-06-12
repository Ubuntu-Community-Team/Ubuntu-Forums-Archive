---
title: "Failing Cedega system tests"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-03-24
I am trying to set up cedega for the first time, and when It runs the system tests, the first one "openGL direct rendering" fails. Also, under the hardware, it is not picking up my graphics card. It is an nvidia card and I have tried installing the "nvidia" driver for it, but whenever I do, X refuses to start, and I have to change it back to get a working monitor. where to start?

---

### Post by igknighted on 2007-03-24
> **HgBoy said:**
> I am trying to set up cedega for the first time, and when It runs the system tests, the first one "openGL direct rendering" fails. Also, under the hardware, it is not picking up my graphics card. It is an nvidia card and I have tried installing the "nvidia" driver for it, but whenever I do, X refuses to start, and I have to change it back to get a working monitor. where to start?

To pass the cedega test you need to get the nvidia driver installed.  What nvidia card do you have?  Also, what methods have you used to try to install the nvidia drivers?  The easiest way is through the repo's.  If those don't work (or if you have a custom built kernel) try the Envy script (choose manual install w/ a custom kernel).  Don't try the ones from Nvidia's site except as a last resort.

---

### Post by zvacet on 2007-03-24
Try with** nv** instead o**f nvidia** and after that install drivers with Envy as recomended.

---

### Post by HgBoy on 2007-03-24
My grapics card is an Asus GeForce 7300GS Pci Express. The method I have been trying is disabling the "nv" driver, installing the "nvidia" driver from the website, editing my xorg.conf file, and trying to restart X.This promptly causes X to be configured improperly, so I have to change it back.  Which driver should I load from the repositories? (And the repos are found using synaptic correct? Im still fairly new)

---

### Post by taurus on 2007-03-24
Use this.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by HgBoy on 2007-03-24
Even though I tried python 4 times the other night, it seems to have worked this time. All of my cedega tests have passed, thanks for the help

---

