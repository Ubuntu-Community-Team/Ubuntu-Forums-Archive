---
title: "VLC in PowerPC Hardy?"
date: 2008-06-21
forum: Apple Hardware Users
---

### Post by lesjohn on 2008-06-21
VLC doesn't work for me at all.  All the audio comes out as static.  Any suggestions?

---

### Post by LunatikOwl on 2008-06-21
First, have you tried other player?
If the Problem is just in VLC try to open different types of audio/video files. Then, if the static is universal try to go to Settings->Preferences->Audio->Output Modules and check the advanced options checkbox. Then you can play with the modules to see if one of them works for you.

Hope it helps

---

### Post by stream303 on 2008-06-21
Which model of ppc mac do you have?

Which card does your ppc box have as shown by the Card Config:

```
cat /dev/sndstat/
```

---

### Post by lesjohn on 2008-06-21
Other players seem to work, so it might not be a real issue.  I get static playing DVDs and .oggs, though I haven't tried any other formats yet.  I'll try playing with the modules like you suggested.  /dev/sndstat contains

Sound Driver:3.8.1a-980706 (ALSA v1.0.15 emulation code)
Kernel: Linux lesjohn 2.6.24-19-powerpc #1 Wed Jun 4 15:27:43 UTC 2008 ppc
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SoundByLayout

Audio devices:
0:  (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: SoundByLayout

Thanks!

---

### Post by lesjohn on 2008-06-21
Setting "Audio output module" to "Linux OSS audio output" seems to have done the trick.  Thanks!  Is this something I should file a bug report for, or is it specific to my system?  It's kind of trivial, but not obvious for a noobie like me. (:

---

