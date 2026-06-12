---
title: "Record PCM?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by DerGeist on 2008-02-09
Hi all,

This question is about recording sound on my laptop computer. It has a webcam and microphone built-in.

This question has been driving me NUTS. I just spent about 4 hours trying to figure it out, and collapsed out of frustration. Anyone who can help is hugely appreciated! :)

All I want to do is record what's coming out of my sound card into some kind of playable format. WAV, Mp3, I don't care, I can convert it later. :p

I tried vsound, but it can't record, as it complains that it can't find "vsound92931.au" afterwards.

I tried installing/using ESD and then piping esdmon to sox, then to a wave file, but I get only silence.

When I use alsamixer to try to select a recording device, I can choose from:

Mic Bypass
Capture
Digital

Capture and Digital are my microphone, so if I enable those for recording all I hear is what's coming from my mic.

So, again, all I want to do is "loopback" what comes from the alsa mixer into a wav file, or mp3 file, whatever. If this can be done with an asoundrc, that would be great too.

In Windows, I just use a program called mp3mymp3..hit record, done. In Mac OS X, there's a program called "AudioHIjack." Is there anything that can record sound directly from the soundcard/speakers/pcm in linux?

Thanks!

Full system specs for reference:

[hp pavilion dv1680us (link)]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00612157&lc=en&cc=us&dlc=en&product=1843699&lang=en")

aplay -l output:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


aplay -L output:

```

default:CARD=Intel
    HDA Intel, CONEXANT Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by benerivo on 2008-02-10
I have done something similar using vlc. If you select File > Open Capture Device...Then in the Advanced Options click 'Stream/Save' and go to 'Settings'. Tick 'File' in the 'Outputs' section, and make a file for the target. Then select Ogg as the encapsulation method and tick 'Audio Codec', selecting 'vorb' for the codec. If you okay all this it will record all sounds in to the target file. At least for me, it records music from Rhythmbox, flash video sounds from Firefox, and sounds from a video in Totem, all to the single file. I haven't the microphone working so i don't know if it would also record that.

---

### Post by typo101 on 2008-02-23
So I had the completely opposite problem. With my audigy card the PCM was captured by default. We wanted to do some studio-esque recording but it doesn't help when the other tracks get mixed into the vocal track automaticlly.

So I fixed that problem, and how I did it might help you.

1. You may need to install the 'asla-utils' package.

```
sudo apt-get install alsa-utils
```

2. run 'alsamixer' in the terminal.

3. Play some music or whatever audio it is you want to capture. Make sure the PCM slider in particular affects actual volume. Once your done the sound check set PCM to 100.

4. Hit F4 to switch to "Capture" mode. If you are lucky (and this tip isn't specific to audigy) you should see a PCM slider on this page. This does not affect PCM output but how much PCM is mixed into the Line in. Set that PCM slider all the way up and you should be in business.

---

