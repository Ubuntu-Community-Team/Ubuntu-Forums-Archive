---
title: "My audio only plays under certain conditions"
date: 2020-02-23
forum: Apple Hardware Users
---

### Post by llamabr on 2020-02-23
Hello, Ubuntu-ers. I triple boot Ubuntu, Debian, and MacOS on my late 2015 27" iMac. If I start a stream or an mp3 using mplayer, I can see mplayer start and the audio start, but nothing plays from the speaker.

However, oddly, if I open firefox and start a youtube video, and then play an mp3 or stream, the audio works. I can then close youtube and play the audio forever. However, if the mp3 ends, I must start the cycle over again in order to hear the next one. I can use alsamixer to control the volume once it gets going.

Here's some output:

```
 brock@phasma:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CS4206 Analog [CS4206 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CS4206 Digital [CS4206 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 12: HDMI 6 [HDMI 6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brock@phasma:~$ 
 
```

```
 brock@phasma:~$ lspci | grep Audio
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
brock@phasma:~$ 
 
```

I appreciate any advice. Thank you.

---

### Post by webaake on 2020-02-23
Do you have pulseaudio installed? If so, take a look in "Sound Settings", when mplayer is running without sound. You can start it from the commandline with: pavucontrol 

I had some issues where different apps were sending sound to different outputs but fixed it in pavucontrol.

---

### Post by ajgreeny on 2020-02-23
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

---

### Post by llamabr on 2020-02-24
> **ajgreeny said:**
> *Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

I do not believe this to be a hardware issue, since I did have good luck messing with pulse. Note that my iMac is really just a big AMD machine running the same software as anyone else. Please put this thread back where you found it. Thank you.

---

