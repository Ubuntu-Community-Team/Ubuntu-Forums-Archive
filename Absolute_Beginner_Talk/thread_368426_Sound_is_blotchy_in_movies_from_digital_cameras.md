---
title: "Sound is blotchy in movies from digital cameras"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by ginnie6 on 2007-02-23
The sound is fine on music but in the movies downloaded from my camera its very scratchy and blotchy. It is fine in windows. Any ideas? Thanks!

---

### Post by capdog on 2007-02-23
I had this problem with movies from my Canon digicam. The format is Motion JPEG with PCM sound, and it sounded like an absolute disaster, all noisy and distorted, when playing through Totem and VLC (i think I have XINE backend).

In the end, what I wanted to do was re-encode the videos so they took up less space. I opened them in AVidemux, and selected a different "sound engine", sorry don't know the correct term... one of them worked proper, it wasn't ALSA, was something else. I then re-encoded them into LAME MP3 and XVID and now they play great.

I would also like to know why the sound engine didn't play PCM properly from the beginning!

p.s. They would play clearly through Avidemux, once the correct output engine was selected.

---

### Post by Rhubarb on 2007-02-23
More information would help here.
What camera do you have, what is the format of the movies your are trying to play?
What program are you running to play your movies?

Try installing vlc from synaptic and play your movies with that.
VLC supports many sound / video formats.

---

### Post by ginnie6 on 2007-02-23
> **Rhubarb said:**
> More information would help here.
What camera do you have, what is the format of the movies your are trying to play?
What program are you running to play your movies?

Try installing vlc from synaptic and play your movies with that.
VLC supports many sound / video formats.

Its a fuji 5200 and the files are avi files. VLC worked! thanks!

---

