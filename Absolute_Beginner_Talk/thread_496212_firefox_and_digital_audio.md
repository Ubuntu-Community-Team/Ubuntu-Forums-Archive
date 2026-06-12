---
title: "firefox and digital audio"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by direwolf08 on 2007-07-08
Hello all:I am trying to get firefox to play audio (from pandora, last.fm, and on vids with youtube) through my computer's digital audio coax output hooked up to my receiver (nvidia HDA-ALC888, digital out: iec958 on ALSA mixer).  Other programs (mythtv, amarok, totem, mplayer, etc) work perfectly with the digi out, but Firefox (and epiphany, for that matter) don't seem to output on the digital out.  I have alsa-oss installed, have updated flash, and I have also fixed the DSP mode in the firefoxrc file as many have recommended.  My problem *appears* to be with firefox trying to use the incorrect audio device, as seen in the following message when I run firefox from shell and try to play a video on Youtube:

```
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM spdif
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM plughw:0,0

```

notice the "Unkown PCM pluginhw:0,0".  I assume that is referring to card 0, device 0.  My digital out is 0,1.  Interestingly enough, I don't hear audio when I plug headphones into the speaker jack, either.  Is there any way to tell firefox to use card 0, device 1 (my digital output)?  

Any suggestions would be appreciated.  thanks!

---

### Post by direwolf08 on 2007-07-10
I am pouring over the Firefox Flash How-To thread at the moment, still no luck . . .

---

### Post by direwolf08 on 2007-07-30
some more info.  

The output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My asound.conf file:
```
pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}
```

---

### Post by dracomordag on 2007-12-26
i am having this exact same issue... any help would be appreciated

---

