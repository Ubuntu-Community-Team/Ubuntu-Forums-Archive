---
title: "xvidcap  - help!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-04-15
I am trying to use xvidcap to capture video/audio from a program. Video works fine, but it never records the audio. I have it set to record from /dev/dsp. Do I need to change this? Please help - i have posted this on several forums and never got an answer.

---

### Post by nautilus on 2007-04-15
no, that's correct, but you also must have your recording source set to PCM.

see, programs play into dsp, which then makes it come out your speakers; but recording that is usually not done, so by default it's off.

(I should mention, you can set this in the mixer program of your choice.  Usually, this looks like a small speaker in the tray.)

---

### Post by rouge568 on 2007-04-17
How do I do this? PCM is set to full volume, and GNOME ALSA Mixer shows no other options for it. Or do I need to set it as source in xvidcap? if so, whaere is the output file?

---

### Post by charly4711 on 2007-04-23
PCM may be set to full volume ... but prolly not for recording, just for playback

---

