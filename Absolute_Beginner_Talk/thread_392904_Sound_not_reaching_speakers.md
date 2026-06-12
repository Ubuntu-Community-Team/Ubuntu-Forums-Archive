---
title: "Sound not reaching speakers"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Cam on 2007-03-25
After many reinstalls, kernel-corrupting, and general hair loss I have discovered that my sound (coming from an Intel HD audio device)  is actually working, but just not reaching the internal speakers of my laptop, rather going straight to the headphone jack.

Is there a way to configure my sound system to use my laptop speakers when nothing is plugged into the headphone jack? I am using kubuntu 6.10.

---

### Post by gilgongo on 2007-03-25
The now-ritual first reply on this: have you dropped to a command line and typed "alsamixer" and un-muted or turned up anything that might be implicated?

---

### Post by floke on 2007-03-25
I have the same problem. Filed a bug report ages ago and apparently now its fixed - but not for me.

---

### Post by Cam on 2007-03-25
> **gilgongo said:**
> The now-ritual first reply on this: have you dropped to a command line and typed "alsamixer" and un-muted or turned up anything that might be implicated?

"PCM and PC speaker" are on full, everthing else is [OFF]

---

### Post by yj09 on 2007-03-26
I also get same problem.. still find out the solution. PCM on alsamixer don't have mute or un-mute. run on edgy 6.10 before not working. and now using feisty still not working.

---

### Post by Cam on 2007-03-26
Anyone?

---

### Post by 1/0 on 2007-04-20
Tried muting SB Live, AC97 and external in alsamixer?

---

