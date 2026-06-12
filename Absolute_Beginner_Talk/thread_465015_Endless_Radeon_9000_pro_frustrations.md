---
title: "Endless Radeon 9000 pro frustrations"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-05
Okay, so fglrx did't work. I found it that there are other drivers that can give me 3d acceleration. I used this guide (guide for using the 'radeon' driver): [https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
to install my new driver. Now the xserver crashes again and says there's no screens found. 

//
Output:

(WW) RADEON: No matching Device section for instance (BusID PCI 1:0:1) found
(**) RADEON(0): PreInit
(EE) RADEON(0): No valid modes found
(**)RADEON(0): FreeScreens
(EE)Screens found, but none have an useable configuration.

Fatal server error: 
no screens found
//

The interesting thing is, that radeon in my xorg.conf is on PCI 1:0:0. So what's messed up here? I did mess with the drivers alot, so i guess something else than xorg.conf is screwed up. I hope somebody can help.

---

### Post by wpshooter on 2007-06-05
When you say "**fglrx did not work**", after you installed fglrx did you go into your /etc/X11/xorg.conf file and change the parameter setting for the video driver section from "**ATI**" to "**fglrx**" and then reboot the machine afterwards ?

---

