---
title: "Sound Qualitiy"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by samasaur on 2007-06-26
I recently switched to Ubuntu, and I'm starting to settle down but one problem is getting in the way. The sound quality just seems to be below how it was when I was using Xp. I have a sound blaster live card, and I was wondering if there are any programs on Linux that is similar to the programs provided by sound blaster live and is there is any way to correct this sound quality problem. Because when the volume is turned up, there seems to be a little squeaky noise. Thanks.

---

### Post by stmiller on 2007-06-27
Open a terminal, and type

alsamixer

and hit enter. Try adjust some levels there, or muting inputs that may be on.

---

### Post by Gary.M on 2007-06-27
Probably the mic input is open and gain cranked up. I had that. Pull the gain back a little on that and mute too if it helps. In general I have all inputs pulled back except PCM on playback...  play around.

---

