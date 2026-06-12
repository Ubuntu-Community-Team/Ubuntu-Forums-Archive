---
title: "spdif/optical audio on Mac Mini 4,1"
date: 2012-08-05
forum: Apple Hardware Users
---

### Post by Raina343 on 2012-08-05
I'm wondering if anyone has actually got this working?  I've read lots about HDMI Audio, and i have that working without any issue.  The optical port on my Mac however seems to be a different story..

I followed the info here [http://ubuntuforums.org/showthread.php?t=1670215#4](http://ubuntuforums.org/showthread.php?t=1670215#4) but that just dumps the audio to the HDMI port.  Even if I modify the 

aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Center.wav 

command to different values (I tried 0,0 0,1 0,2 0,3 0,4 0,5 0,6 0,7 0,8)

All of them except 0,0 output through HDMI

has anyone got it working properly?

---

