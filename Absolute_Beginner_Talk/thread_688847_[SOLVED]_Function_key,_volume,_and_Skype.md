---
title: "[SOLVED] Function key, volume, and Skype?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-02-05
Hey all,
I just installed Skype on Ubuntu 7.10. Via Alsa Mixer/Volume control, I added the Mic Boost and Mic Capture switches (I couldn't hear my voice before).

Now, my usual keyboard combo for increasing the volume, function + page up, increases the volume of the mic rather than the speakers. So, I've lost keyboard control of volume up (FN + pg. up), volume down (FN + pg. down), and mute (FN + End).

Any ideas?

---

### Post by neurostu on 2008-02-05
What hardware are you using?

---

### Post by psoulocybe on 2008-02-05
System -> Preferances -> Sound

Make sure Master is highlighted at the bottom.   I had a similar sounding problem a few months ago... This had something to do with it for me.

---

### Post by jaredssix on 2008-02-06
Thanks guys, you led me in the right direction, and know the situation in SOLVED!

From System>>Preferences>>Sound, under the Devices tab I set Audio Conferencing, Sound capture to my soundcard, Intel ICH6 (it had been set to ALSA).

Thanks again,
Another victory for the forums!

---

