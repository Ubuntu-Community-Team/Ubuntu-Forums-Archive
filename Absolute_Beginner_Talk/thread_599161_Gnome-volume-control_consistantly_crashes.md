---
title: "Gnome-volume-control consistantly crashes"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-11-01
Since gutsy, i've had an annoyance with the gnome volume control. One day it crashed, and never re-appeared. Running it manually gives these results:



paul@paul-desktop:~$ gnome-volume-control

{seems to work fine, leave it up in the background, and within  few minutes, this happens, same crash every time} 

gnome-volume-control: simple.c:370: snd_mixer_selem_get_playback_volume: Assertion `(elem)->type == SND_MIXER_ELEM_SIMPLE' failed.
Aborted (core dumped)


Anyone else enountered this? Or better, fixed it?

---

### Post by alienexplorers on 2007-11-01
Try reloading the ALSA Mixer.

---

### Post by Paulmd on 2007-11-01
> **alienexplorers said:**
> Try reloading the ALSA Mixer.

What's the correct procedure?

---

