---
title: "Wireless LAN setup"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by billtemp on 2005-09-05
I am a new Ubuntu user, and am trying to set up a wireless LAN with a USB Netcomm device.

I can see the USB device listed in the device listing as the correct 802.11 listing, but I only have a modem listed in the networking area.

Some info I have from wiki.ubuntu suggests:

"It should be noted that Ubuntu comes with an earlier version of the ndiswrapper kernel modules that are pre-compiled. Many users find success by simply using these. To see if the precompiled modules work for you, simply install the ndiswrapper-modules and ndiswrapper-utils packages from the Synaptic Package Manager and skip the steps below in the "Compiling from Source" section. "

I think I should try the pre-compiled modules, but I can find the '-utils' package and can install it, but can not find the '-modules' package.

Can anyone help?




Ubunto 5.04

---

### Post by Arjen on 2005-09-05
I think that is an error in the wiki. I am using ndiswrapper myself, and only have the -utils package installed as well. You can probably just skip that and continue with the hints as given in the wiki, although I found another one that might be easier.
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

### Post by Steve1961 on 2005-09-05
You should be fine with the utils package, although I've never gotten it to work.  If it doesn't work I'd suggest downloading ndiswrapper 1.2 source - this seems to be a much better version.  See the thread below for how I got this working with a broadcom card.

[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)

---

