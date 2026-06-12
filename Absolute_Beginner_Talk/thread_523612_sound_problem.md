---
title: "sound problem"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by atomkarinca on 2007-08-12
this is getting really embarrassing for me. i installed ubuntu on my friend's computer and now i can't get the sound working. i have tried everything i know. there seems to be no problem with the driver and all but it's not working.

here are some outputs:
> 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> asoundconf list
Names of available sound cards:
ICH6

i tried everything in this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i had sound with the live cd so i thought there wouldn't be any problems but i was wrong. i checked alsamixer, too with no luck.

only error i can get is with rhytymbox:
> 
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default

can anybody help me?

---

