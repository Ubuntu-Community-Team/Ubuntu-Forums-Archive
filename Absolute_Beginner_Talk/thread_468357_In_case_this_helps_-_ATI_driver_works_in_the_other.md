---
title: "In case this helps - ATI driver works in the other kernel"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-08
Hi,
I thought I should share this in a separate post because it's unusual enough and it may help someone...or me.

I have an ATI X-1650 Graphics card - I originally bought it for Vista because my Nvidia was acting kinda flaky with it.

I'm a non-coder but I'm not scared to use the terminal when I have to and I tried a lot of things to get the ATI accelerated driver going. Finally, someone told me about ENVY [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) . 

Envy worked for me in a strange way though. I used it to install the ATI Driver, but I was still getting blank screens on the reboot - until, .....I simply tried booting into a different kernel. Voila!

In other words, I would do the ATI install (with Envy) on one kernel, but it would install successfully only in a different kernel. If I reboot to the same kernel, I get a blank screen, but if I reboot and choose a different kernel, my screen resolution is higher and the ATI seems to be installed successfully. 

I'm interested to hear any comments because I do find this suspect. But after considering that with my widescreen monitor, I have to have 1680 x1050 resolution to browse correctly, I finally decided that I'll take this solution, however partial it may be.

I actually have an Nvidia GeForce 7300 LE card, but when I tried plugging that in and used ENVY to install the driver, I could not get 1680 resolutions to show up AT ALL. So I put the ATI back in.

I just wanted to share this experience - maybe it can help our situation somehow....

Many Thanks, Frank B.

---

### Post by DBStevens on 2007-06-10
Binary video drivers frequently only work correctly under a small number of kernels (sometimes on only one kernel version) this is one of many reasons that the linux kernel programmers will ignore error reports if the kernel taint flag is on.

Here what you downloaded didn't work with the kernel you were running when you downloaded the driver but did on another kernel version you had on the system.

It is also posible that the download script thought the other kernel was the one to do the download for so it downloaded the wrong one.

I gave up trying to play the binary video driver routine a long time ago.

---

### Post by Brightbelt on 2007-06-11
There's actually more to report here. Just recently I installed Mandriva in order to try a possible alternative to Ubuntu, but I didn't like it, so I reinstalled Ubuntu from scratch again. 

Knowing about Envy this time allowed me the option of doing the ATI install right away before anything got changed in the system.  And it turns out, THIS REALLY WORKED. 

The ATI install worked correctly on the same kernel I installed it on, and I had the right resolution.  So it's nice to know it works and to have that part behind me.

Thanks, ...Frank B.

---

