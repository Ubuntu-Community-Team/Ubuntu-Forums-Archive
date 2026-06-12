---
title: "MacBookPro9,1 won't go to sleep when lid is closed"
date: 2013-10-03
forum: Apple Hardware Users
---

### Post by sgehlich on 2013-10-03
Hey,

I just installed Ubuntu 13.04 on my MBP9,1, and everything works fine except for the power management. Even though my power settings say that the machine should suspend when the lid is closed, it doesn't. The screen turns off (the apple on the back of the lid turns off) but the machine keeps running.

Any hints?

Thanks!

---

### Post by keshavtek on 2013-11-03
Same here .
I have MBP 9,1. I have ubuntu 13.04 installed. RefInd is the bootloader. I seen posts where people said it is due to nVidia Video Adapter.
Any luck?


> **sgehlich said:**
> Hey,

I just installed Ubuntu 13.04 on my MBP9,1, and everything works fine except for the power management. Even though my power settings say that the machine should suspend when the lid is closed, it doesn't. The screen turns off (the apple on the back of the lid turns off) but the machine keeps running.

Any hints?

Thanks!

---

### Post by mpbishop on 2013-11-05
Hey all,

I experienced this exact same issue with my MBP 8,2 that you are also describing happened on your 9,1. The laptop would not go into 'suspend' mode when the lid was closed, even though Power Settings was set to enable that feature.

I can't say for certain if this will fix your problem or not, since I'm using an 8,2 - however, the problem for me ended up being the proprietary fglrx video drivers that were in use, which I had enabled for the purposes of comparing performance of the 3D acceleration capabilities that they offered to the open-source xserver-xorg driver. As soon as I switched back to the xserver-xorg driver and rebooted, my MBP suspended like normal again when the lid was closed, and also woke up instantly as well when opened again.

I know that the 9,1 has an nVidia chip instead, whereas my 8,2 is an ATI chip, but my understanding is that you also may have two video driver options as well. Might be worth checking out and trying to change them to see if the problem is fixed or not.

---

