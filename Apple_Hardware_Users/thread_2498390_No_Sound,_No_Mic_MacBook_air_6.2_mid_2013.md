---
title: "No Sound, No Mic MacBook air 6.2 mid 2013"
date: 2024-06-11
forum: Apple Hardware Users
---

### Post by aink99 on 2024-06-11
Hi running Ubuntu noble 24.04 on my MacBook Air 6.2 mid 2013.

Everything seems to be working except the speaker sound and mic. I only have a dummy audio interface showing in my configuration.

I've an alsa-info 

[http://alsa-project.org/db/?f=4eff7e68652155008f151a715eb22e5aa900fc99](http://alsa-project.org/db/?f=4eff7e68652155008f151a715eb22e5aa900fc99)

aplay -l # Shows HDMI output for some strange reason there's no hdmi port on a macbook air 6.2 .





**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



----

Does anyone on this forum have the same issue?

---

### Post by howefield on 2024-06-12
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by fullyguts on 2024-08-16
Hi, I have a late 2013 Mac-book Air 6.2 and have no sound issues, have you checked in the system settings?

---

### Post by aink99 on 2024-08-21
I'm not exactly sure what happened, but after trying so many things, it finally worked. I heard the characteristic Mac startup chime for the first time , and now everything is working

---

