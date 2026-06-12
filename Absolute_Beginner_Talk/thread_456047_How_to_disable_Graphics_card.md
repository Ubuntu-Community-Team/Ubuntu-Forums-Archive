---
title: "How to disable Graphics card"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-05-27
Please help I need to diable desktop effects for ubuntu 7.04 as my nvidia fx 5700le graphics card clapped out when I enable it. (after ubuntu did the download and restart) now I'm stuck and the screen just goes black.( but can still hear the start up )

---

### Post by arijarot on 2007-05-27
> **fongs said:**
> Please help I need to diable desktop effects for ubuntu 7.04 as my nvidia fx 5700le graphics card clapped out when I enable it. (after ubuntu did the download and restart) now I'm stuck and the screen just goes black.( but can still hear the start up )

try ```
sudo nvidia-glx-config disable
```

---

### Post by fongs on 2007-05-27
thanks for quik response shal try it.

---

### Post by fongs on 2007-05-27
Hmmm, well I've got a Radeon 9200 card. Right now I'm displaying in 1280x1024, but I could go up to 1600x1200 if I wanted. All I did was sudo dpkg-reconfigure xserver-xorg, choose all the defaults until I got to the resolution screen. Then I hit the space bar to choose my resolutions and restarted the xserver with ctrl+alt+backspace.
__________________
Ubuntu User #11392
 thanks all found this helped still can't get graphics card to work GeForce fx5700le. Any guidance or someone who has got this graphics card to work 3d, would be greatly appreciated.

---

