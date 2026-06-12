---
title: "Sound problem with games"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Willie G on 2007-03-26
If I play one of the games that I installed through the synaptic package
manager, I can get the game audio to play properly.  If I install a game 
or game demo other than through synaptic I get no audio whatsoever.
How can I remedy this?

Ubuntu 6.10
Audio device: nvidia mcp51 audio

Installed packages:
alsa-base
alsa-oss
alsa-utils
libasound2
libsdl1.2debian
libsdl1.2debian-alsa
libsdl-image 1.2
libsdl-mixer 1.2

---

### Post by MethodOne on 2007-03-27
What game do you want sound in?  If it's Doom 3 or Quake 4, try running the following command in the terminal (Applications, Accessories, Terminal):
```
[I]d[I]oom3 +set s_driver oss
quake4 +set s_driver oss[/I][/I]
```

---

### Post by Willie G on 2007-03-27
> **MethodOne said:**
> What game do you want sound in?  If it's Doom 3 or Quake 4, try running the following command in the terminal (Applications, Accessories, Terminal):
```
[I]d[I]oom3 +set s_driver oss
quake4 +set s_driver oss[/I][/I]
```

I am trying to run the demo for Descent3.  I tried using +set s_driver oss and this didn't work. 
I also tried echo "descent3_demo.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
in the terminal, using the command line +set_initsound 1, running "killall esd", and using the command sudo echo "et.x86 0 0  direct" > proc/asound/card0/pcm0p/oss
and none of these worked

Also, in sound preferences if I try to set the devices as oss, not only will I not get sound when I test it but the sound utility will freeze up on me.

---

