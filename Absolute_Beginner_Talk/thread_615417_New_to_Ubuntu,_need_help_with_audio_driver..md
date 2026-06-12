---
title: "New to Ubuntu, need help with audio driver."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by dormot on 2007-11-17
I'm new to ubuntu and the install went fine and everything. The only problem is that there is no sound and I can't fix it. I have a HP compact dvxxxx Convertible tower series, forgot the specific model number, and the built in sound card is a Realtek AC97. I've tried some tutorials and the only thing I was able to do is get sound from the built in speaker in the MOBO. The mic, headphone, etc don't work and I'm getting a little frustrated. What I did if I recall correctly was:

gedit /etc/modprobe.d/alsa-base

and added

snd-hda-intel model=3stack

that's how I got the sound from the internal speaker. Help would be greatly appreciated and I really don't want to go back to windows because of this minor glitch. :(

---

### Post by zhaozhou on 2007-11-17
If you get sound at all, its probably not the driver thats the problem.

Have you tried looking into the mixer state (alsamixer or any other volume control)?

---

