---
title: "Updates kill xserver boot"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-03-19
When I install the following updates

linux restricted modules-2.6.17-11-386

linux restrcited modules common

(It is possible it is just one of these that causes the problem) I can no longer boot properly. there is an xserver problem on boot, it can no longer load the nvidia driver 

fatal server error:
no screen found
could not open /lib/modules/2/6/17-11-386/volatile/nvidia.ko
failed to load NVIDIA kernel module

Is this a problem with the updates or my setup? What is an easy way of fixing it. I solved the problem by restoring my system backup and ignoring those updates for now, but is there a better way? Thanks.

---

### Post by Kobalt on 2007-03-19
How did you install your nvidia drivers : through Synaptic or with the nvidia package (meaning you use the beta drivers) ? 
I have used the nvidia package and after each kernel update I have to install it back again from the CLI otherwise X won't start...

---

### Post by Patrick K on 2007-03-19
I have to reinstall the drivers, too. I find the Envy script to be a big help in this.

---

### Post by luvinit on 2007-03-19
Ah, I see. I installed the driver via envy. Now, if I want to update, do I install the restricted module updates first, then run envy again before a reboot?

---

### Post by Charles Hand on 2007-03-19
What is an "envy" script?

---

### Post by kpkeerthi on 2007-03-19
Check this out [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

