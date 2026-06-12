---
title: "Asymmetrical sound"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-04-17
Hi 

Can anyone explain why, when using Internet telephony - Skype, Ekiga, Sipgate (x-lite), I've tried them all - the sound level from my microphone is much lower than the sound coming from my speakers. I've tried two different mics, and every control of the mic sound level, in Volume Control, within the VOIP application, and on the mic, is at the maximum level.

Regards

Roger D

---

### Post by bodhi.zazen on 2007-04-17
Not sure if this will help or not, but when I am having trouble with sound I use alsamixer.

Open a terminal and type alsamixer.

You can use the tab keys to cycle through options.

For your microphone you are looking for capture, increase capture with the up arrows and see if it helps.

---

### Post by Roger D on 2007-04-17
Thanks

I've already set capture to maximum using gnome ALSA Mixer. I checked from the terminal and alsamixer, but it was already 100%

---

