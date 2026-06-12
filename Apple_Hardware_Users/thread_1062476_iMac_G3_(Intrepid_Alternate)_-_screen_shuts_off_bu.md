---
title: "iMac G3 (Intrepid Alternate) - screen shuts off but power button stays on, bad noises"
date: 2009-02-06
forum: Apple Hardware Users
---

### Post by Cyanaether22 on 2009-02-06
Hey, I've FINALLY managed to install Ubuntu Linux PowerPC 8.10 Alternate on my iMac G3 350MHz slot-loading Bondi Blue machine.

Now the problem I'm having is that when I boot from the computer (with L for linux), it gets to the "Loading..." screen and then the computer shuts off, all except for the power button which stays lit up yellow... and the computer makes really weird noises that don't sound good AT ALL.

I thought this could be the xorg.conf file that has the wrong video configuration... but I was having trouble editing the settings there, I had to enter Repair Mode... at one of the steps (sorry, not sure which one it was), it asked me which folder was the root folder, and there were 4 options.... /root/dev1, /root/dev2, etc all the way to dev4. This could be because I had to make a few tries on the install.... would this be causing the problem?

Please help!

---

### Post by nkbj on 2009-02-07
It is a problem with the boot splash screen. It is described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/216666](https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/216666)

---

### Post by Cyanaether22 on 2009-02-07
Thanks - so just to confirm, this is NOT RELATED to the xorg.conf file? I've done a lot of random stuff to try and get my xorg.conf working because I thought that would solve this problem.


I managed to boot up with Linux video=ofonly, it says it's in Low-Graphics Mode and I should edit my xorg.conf file to make it work with my hardware. My hardware is iMac G3 Bondi Blue 350MHz Slot-Loading with an ATI Rage 128 VR. No xorg.conf I've found posted online has the right specs that work for me, I've tried lots of different combinations... resulting in various errors from "Input device, screen, and graphics card could not be detected. You have to configure them manually" to "No framebuffers, blablabla" to "No devices found."

But if the xorg.conf isn't the problem then I guess I should just put video=ofonly in my yaboot.conf and live with low-graphics mode...

---

### Post by nkbj on 2009-02-08
The problem does not have anything to do with the xorg.conf file. The problem with xorg.conf is described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/22976](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/22976)

---

