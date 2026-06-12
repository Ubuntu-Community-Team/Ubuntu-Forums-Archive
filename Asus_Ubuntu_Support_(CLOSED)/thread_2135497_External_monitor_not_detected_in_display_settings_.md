---
title: "External monitor not detected in display settings Asus N56VM S4089V"
date: 2013-04-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Staarlite on 2013-04-14
Hi,
The specs on the website I bought the laptop from say I have a Dedicated NVIDIA Geforce GT630M with 2 GB dedicated memory.
I've not yet dowloaded any proprietary drivers as from everything I've read I don't know if I need it or not to be able to view my laptop on an external monitor.  I dual boot and in Windows I am able to mirror displays using hdmi port - in Ubuntu when I click "detect displays" nothing happens.  What do I do from here to get this working?  I am using Ubuntu 12.04.2 with 64bit.
FYI 

sudo lshw -C video | grep product:

brings up:

product: NVIDIA Corporation
product: Ivy Bridge Graphics Controller

And 
lspci | grep VGA

brings up:
VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)

Any help you can give to get this working is appreciated - otherwise I have to close ubuntu and boot back into windows to use this facility!

---

### Post by CSNate on 2013-04-28
The N56 is an Nvidia Optimus laptop, you're going to need to install bumblebee.  [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)  There are issues using HDMI out with bumblebee in Linux, its doable, but you're going to lose the power saving feature that Optimus provides.  I believe the next driver release from Nvidia is going to have Optimus support builtin and hopefully support for the use of HDMI ports.

---

