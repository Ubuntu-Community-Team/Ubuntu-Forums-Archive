---
title: "how to change ATI card to nVidia card"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by PPisHere on 2006-02-16
Hi There,

I am using old ATI card in my system and now it running old. My plan is to change the display card to nVidia card. It seems to be prefered card in Linux systems :) 

What do I need to take in consideration in installing point? What should be removed, I mean drivers and what is needed to installed with new card?

Or is it all just that I remove the old card and plug-in a new one and that's all? :confused:

---

### Post by mr_pouit on 2006-02-16
I think you can do :
- remove ATI fglrx proprietary drivers (if you installed them)
- install the nvidia proprietary drivers (only if you need them)
- reconfigure your graphical interface : type in a terminal
```
sudo dpkg-reconfigure xserver-xorg
```
- let the defaut choices, but choose the NV or NVIDIA driver when asked 
- Shutdown
- Remove the old card and plug the new card
- Reboot

and it should work. If it doesn't, try reconfiguring xserver-xorg with the vesa driver (a generic driver) for example.

---

