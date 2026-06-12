---
title: "Installation problems."
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Invisible on 2007-11-10
OK I am having a problem, a fairly annoying problem and I would like some help please. 

My problem is this: I have installed Ubuntu on a Duel Core, Duel Graphics/SLI system which has a total of 4 monitor outputs (2 analog and 2 digital, one of each on each card). 

the cards I am using are NVIDIA 7800's GT's. However when I come to start Ubuntu, the computer shows the start up screen on card 1. And the ubuntu startup screen shows on card 1. However the ubuntu Log on screen randomly chooses a monitor port with which to start up on. And so I have to move my monitors from one port to the next to find out which output ubuntu has decided to display on. 

And when I use the screen and graphics to select the monitor/card to use, I log off and the whole process repeats. 

This is getting very very annoying. So please help.

---

### Post by zippy028 on 2007-11-10
If you are using the NVidia 3D drivers and the nvidia settings manager you might try to use the settings mgr. to save your working X config to xorg.conf.
from a terminal:
```
/sudo usr/bin/nvidia-settings
```

---

