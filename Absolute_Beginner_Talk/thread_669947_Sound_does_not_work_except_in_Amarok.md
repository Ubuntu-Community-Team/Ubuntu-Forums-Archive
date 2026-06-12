---
title: "Sound does not work except in Amarok"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by dstickst on 2008-01-16
I just installed Gutsy and its software updates, etc. on my machine a while ago. My only issue is that for some reason, I can hear music played through Amarok perfectly fine, but any other sound sources (system, games, youtube, etc.) are silent. When I test my sound using the Sound window in System->Preferences I can hear all the tones. However, when I go to the "Sounds" tab and try to play the Login/Logout sounds - nothing. My current devices are set to Intel ICH6, which seems to be the only one that works at all.  I'm by no means comfortable noodling around in the terminal, so any advice would be appreciated.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by bschleusner on 2008-02-23
use "asoundconf -set-default-card" to set your default card and see if that works.

---

