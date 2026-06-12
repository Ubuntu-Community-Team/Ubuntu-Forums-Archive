---
title: "No sound in Flash, VLC"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-10-28
My sound works, but only on things like startup sounds and in Movie Player. My problems are with VLC and Flash; they won't play any sound at all. Any ideas how I can fix this? Thanks

---

### Post by daimaru on 2007-10-28
i had same problem cause i use usb headphones. don't know with flash but for VLC: in vlc i went to settings --> audio --> output modules --> alsa and selected my headphones usb  form the alsa device list (hit refresh list if you dont see your soundcard)

---

### Post by Tom B on 2007-10-28
I have the same problem. Amarok, movieplayer, last-exit, and pidgin all do sounds normally, but flash videos and vlc don't. When I try to play a video with vlc I get ```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000337] oss audio output error: cannot open audio device (/dev/dsp)
```
I have tried looking at some guides but I still have no idea what this means.

---

### Post by alwiap on 2007-10-28
> **daimaru said:**
> i had same problem cause i use usb headphones. don't know with flash but for VLC: in vlc i went to settings --> audio --> output modules --> alsa and selected my headphones usb  form the alsa device list (hit refresh list if you dont see your soundcard)

that worked for my C-Media USB soundcard (Icemat Siberias), thanks!

---

### Post by quick_nick on 2007-11-06
im having the same problems in VLC

here is the output from vlc
```

ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000337] oss audio output error: cannot open audio device (/dev/dsp)
[00000337] main audio output error: couldn't find a filter for the conversion
[00000337] main audio output error: couldn't create audio output pipeline
```


ANYONE HELP PLZ!!

---

### Post by theovercoat on 2007-11-08
what is your vlc audio output set to now?  i leave it at default and it works everytime with my usb soundcard.

---

### Post by quick_nick on 2007-11-08
i tried alsa and oss.  I am going to do a complete re-install.  If i open the sound app and try to test either alsa or oss it sends an error as well.  I would post the error  but im on my windows boot right now.

I am using a Toshiba satellite a105

---

### Post by priyank_bolia on 2008-06-27
I am having the same issue, I am able to hear voices in vlc and flash in my dell laptop, but when I plug my usb headphone, it don't use them, no matter whatever i set in the vlc or the sound preference

---

