---
title: "Ubuntu and Drivers"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-04-24
Hi, I just installed Ubuntu, and before I really get into things here, I want to make sure all my device drivers are up to date.  How is that handled in Ubuntu/Linux?  Should I go to all the hardware manufacturers and check for Linux drivers?  Are driver versions listed in the hardware profile?  I already installed Envy, so I'm wondering if all other hardware is handled this way.  I'm just a little overwhelmed right now, and some help would be appreciated.

Thanks!

---

### Post by Titus A Duxass on 2007-04-24
If your devices work then the correct driver is already installed.

If any device (WLAN cards) does not work then further research (searching the forum) is required.

---

### Post by Tomosaur on 2007-04-24
The way drivers work is a bit different under Linux. If your device is working, you already have the drivers. Good device drivers are normally written right into the kernel - meaning your device will work with no extra setup. This is not true for all drivers though. Things like graphics cards you may need to sort out yourself. If you have, say, an nVidia card, you may well want to download the nVidia drivers yourself from their website. Linux does have an nVidia driver, but it is not as powerful as the 'official' nVidia one.

In short - you may need to manually install drivers for brand new hardware, as there is always a bit of a delay before the open-source driver for it is ready. Older hardware - there's a good chance the driver is already there. The easiest method by far is to just plug it in and see if it works.

---

### Post by Rob2Kx on 2007-04-24
Thanks for the quick replies.  So there's no need to update drivers then?  Once I have one working version of it I'm set?

Thanks again.

---

### Post by ofek on 2007-04-24
The real question is why would u want to replace a perfectly working driver ....
When something just work then it just work no need to tinker with it.
As for the nvidia part, the open source driver is good but not as a good as the closed sourced made by nvidia. People who want some enhanced graphics and hardware acceleration should really use the closed sourced one, though I use the "nv" driver and it suits my needs wonderfully.

---

### Post by silverglade00 on 2007-04-24
For the most part, any driver updates will be done through Update Manager. Most drivers are in the kernel, so any updates will come when a new kernel is available. For things like nvidia cards, just install nvidia-glx from the repos and it will get updated as new drivers become available as well. 

The only time you should have to go outside the repo is for very new hardware. For instance, some newer sound cards get detected as needing the snd-hda-intel driverand only the latest alsa supports it. You might have to compile it from the source code to get sound working. When the version in the repos catches up, you can just get your updates from there.

---

