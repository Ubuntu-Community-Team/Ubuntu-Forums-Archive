---
title: "Sound stopped working"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by t.achim on 2007-04-28
Hi,
I just upgraded to Kubuntu 7.04, and sound has stopped working. I had this problem before, and I unmuted PCM and it worked, but now PCM is not muted and there is still no sound.
However, when I change the volume from KMix, I can hear static at the corresponding volume.
I have a Dell SoundBlaster Live! sound card which came OEM with my Dell.
output of lspci:
02:00.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X

How do I fix this?

---

### Post by t.achim on 2007-04-28
Fixed...[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189)

---

