---
title: "sound - buzzing"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by izua2 on 2007-01-11
i'm using kubuntu 6.06
whenever i start kde, a high pitched sound starts buzzing.

the interesting thing is that now I can play music, and switch volumes from amarok and other players.

if i mute-unmute "front" from alsa mixer, the buzzing stops, but I can't hear any other sound, either.

what should i do?

---

### Post by carlosfocker on 2007-01-15
Check the pcm levels in alsamixer.  I had this happen when pcm was set to 100%.  Try setting PCM to about 60% and see if the buzzing stops.

---

### Post by kolslorr on 2007-04-07
Sorry it doesnt work, buzzing continues.

In alsamixer I only had master, pc speaker and pcm turned on, the rest are off.

---

### Post by ComplexNumber on 2007-04-07
> **izua2 said:**
> i'm using kubuntu 6.06
whenever i start kde, a high pitched sound starts buzzing.

the interesting thing is that now I can play music, and switch volumes from amarok and other players.

if i mute-unmute "front" from alsa mixer, the buzzing stops, but I can't hear any other sound, either.

what should i do?
do you have an inbuilt sound card as well as your main sound card?

---

### Post by nhandler on 2007-04-07
For me, I turned the Master bar down to about 50%. I was still able to listen to all forms of media just fine (they were loud enough), and it stopped the buzzing.

---

### Post by kolslorr on 2007-04-08
Solved with this,
[http://ubuntuforums.org/showthread.php?p=2420191#post2420191](http://ubuntuforums.org/showthread.php?p=2420191#post2420191)

---

