---
title: "Sound driver installation"
date: 2011-12-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Butters94 on 2011-12-19
Ok so I just recently installed ubuntu (11.10 i believe) and found a place that describes roughly how to install windows drivers for use on ubuntu. My problem is that it wants an INF format and on the asus website it's some 3 part executable B.S.. So i guess my question is: Is there an INF file out there and if so how would I go about installing it or if not where do I go from here?

System info:
Ubunto 11.10
Asus P5GDC-V Deluxe
Intel P4 dual core 3.0ghz
using onboard soundcard
just ask for any additional info and i will try to supply it, thanx!

---

### Post by Buntumatic on 2011-12-19
Open a terminal and do ```
lspci -nn | grep -i audio
``` post the output. 
You may need to do sudo -i first.

---

### Post by Butters94 on 2011-12-20
After typing that in it shows this:

00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)

Also i found the IFN or whatever i was looking for and successfully used ndiswrapper to install 2 drivers 1 of which it says is invalid, but i don't think that's a problem. I still have no sound though and have tried many things on the ubuntu troubleshooting page, but I am a noob to ubuntu so idk for sure if i did it all right. Thank you very much for your help.

---

### Post by Buntumatic on 2011-12-21
Now I should say do ```
aplay -l
```Note what chip is used and reconfigure your kernel enabling support for that chip. However, this is not exactly Ubuntu way.
I do not think using ndiswrapper for ALSA will work, at least it never even crossed my mind.
Furthermore, are you sure Ubuntu did not load correct driver for your audio? Often the problem is just solved by turning on required options in mixer.

---

### Post by Butters94 on 2011-12-22
ok it gave this:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but i'm fairly new to ubuntu and dont know how to get into the mixer or reconfigure kernels and stuff. I'll work on it through google-my lord and savior-. I believe the drivers are not the issue as i typed a command into the terminal and the tutorial that supplied the command said if a hage list is outputed then the drivers are right.

---

### Post by Butters94 on 2011-12-22
i opened the mixer and pushed F6 and selected "0 HDA Intel". my other options are default and enter device name. is there anything else i should do because i still hear nothing and i know the speakers and stuff are fine because i use windows regularly on the same HD using dual boot.

---

### Post by Buntumatic on 2011-12-22
Hmmm ... what is the output of ```
strings /lib/modules/`uname -r`/kernel/sound/core/snd.ko | egrep 'Advanced Linux Sound|ALSA'
```

---

### Post by Butters94 on 2011-12-23
ALSA
<3>ALSA card file remove problem (%p)
Advanced Linux Sound Architecture Driver Version 1.0.24.
description=Advanced Linux Sound Architecture driver for soundcards.
description=Jack detection support for ALSA

---

### Post by Butters94 on 2011-12-23
So if i were to aquire a new soundcard that fit into my asus P5GDC-V Deluxe what would you recommend? Or should i maybe try to downgrade to 11.04? Because I'm starting to feel like I've tried everything. I could probably try a new soundcard first since im sure I have one laying around or I'll snag oune out of my cousin's PC haha.

---

### Post by Buntumatic on 2011-12-23
This chip should work with your version of ALSA.
Would you try latest Knoppix and see if it can make any sound?
Would you try alsamixer from CLI, hit F5 and see if anything is disabled that shouldn't be? You may need to use arrow right to see all controls.

---

### Post by Butters94 on 2011-12-23
in the alsamixer nothing is muted and the bars I can adjust are at 100%. I cannot adjust any of the bars except PCM, Beep, and the capture options for some reason.

---

### Post by Buntumatic on 2011-12-23
What's the output of ```
amixer
```

---

### Post by Butters94 on 2011-12-24
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Center',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Side',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [0.00dB] [off]
  Front Right: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 30 [100%] [45.00dB] [on]
  Front Right: Capture 30 [100%] [45.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 30 [100%] [45.00dB] [off]
  Front Right: Capture 30 [100%] [45.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Front Mic'

---

### Post by Butters94 on 2011-12-25
Well I'm sorry and don't want you to feel like your kind efforts were futile, but its christmas day and I seem to have aquired a new laptop which i will be using as a desktop replacement. Ubuntu seems to run quite well on here with no sound or video issues. I of course will try to pay it forward by helping others on these forums, and I'm sure I'll run into issues in the future that I will solve on here. Thank you so much for all of your help and have a Merry Christmas. (unless of course you read this after today, haha)

---

