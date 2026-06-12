---
title: "Random freezing up solved"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Hairyred on 2006-07-28
This may help some others with this problem, random freeze, pixels sticking to mouse pointer, pointer turning into square block etc. I installed the correct nVidia video driver in place of the Ubuntu default nv generic driver and no problems since. In the terminal I typed sudo dpkg-reconfigure xserver-xorg and followed the prompts, choosing the default answers until I reached the list of drivers. I chose 'nvidia' NOT nv and that took me to a list of video card types. I chose mine, the nvidia mx440, and Ubuntu downloaded the appropriate driver and installed it.  All of the correct settings for my card were auto detected, it was too easy! No more freeze ups since! :D

---

