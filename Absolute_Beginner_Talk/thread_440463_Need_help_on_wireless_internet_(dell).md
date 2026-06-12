---
title: "Need help on wireless internet (dell)"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ckmcm04 on 2007-05-11
I am currently using a Dell computer with a wireless USB adaptor [Dell Wireless 1450 Dualband (802.11/a/g/b) USb 2.0 Adaptor]and that is how I get my wireless internet from my router. The USB adaptor works fine when in windows XP. But when I log onto Ubuntu, the USB wireless receiver doesnt even turn on (the lights are off). I know that there should be some drivers that I need to install in Ubuntu to get the wireless adaptor to work. As I am pretty new to Ubuntu, can anyone explain to me the steps on how to set up my USb adaptor. Thanks.

---

### Post by oilchangeguy on 2007-05-11
linux tends not to play well with usb adapters. is this computer a laptop, or desktop?

---

### Post by ckmcm04 on 2007-05-11
It's a desktop (dell dimension 3000)...

Is there anyway that I could get the USB adaptor to work in Ubuntu?

---

### Post by oilchangeguy on 2007-05-11
you'll probably have better luck with an internal pci wireless card. is there no way to connect this desktop via wire?

---

### Post by ckmcm04 on 2007-05-11
it would be rather difficult to connect the desktop via wire as we only r sharing a wireless network in a pretty large house.. :( 

so it seems like it would not be possible to get the USb wireless adaptor to work unless I get an internal wireless card instead???

---

### Post by Teamgeist on 2007-05-11
This seems to be a Broadcom card. Those always cause trouble. 
Try installing the package bcm43xx-fwcutter.
If that doesn't work take a look here:
[http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946)

---

