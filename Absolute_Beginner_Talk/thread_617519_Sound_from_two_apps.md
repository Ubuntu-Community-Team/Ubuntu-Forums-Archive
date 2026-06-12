---
title: "Sound from two apps"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Larken on 2007-11-19
I am new to Linux, so I'm not sure if this is normal behavior or not, but when I have an application like a game, that is already utilizing the sound card, if I open Totem and try to play music in the background, it won't work.  Likewise, if I have Totem open playing music and I launch the game, I will have music, but no game sound.  Is this normal?

---

### Post by click4851 on 2007-11-19
sadly for a default Ubuntu install yes, that is normal. The ability of two apps to have access for sound is often called sound mixing, and Ubuntu needs, in my opinion a little more refinement in that regard. There are many ways to achieve what you would like, trying searching for ALSA and PulseAudio and soundmixing. Good luck

---

### Post by hanzomon4 on 2007-11-29
It should work with most setups by default. But I agree sound in linux **when it does not work** is a pain to fix.

---

### Post by KhaaL on 2007-11-29
Hopefully this kind of issues will  be history with hardy heron and the use of PulseAudio server!

---

### Post by FuturePilot on 2007-11-29
PulseAudio should fix this.

---

### Post by Anthony M on 2007-11-29
I too suffered from this problem. The fix was simple in my case though. In the Preference>Sound dialog I had to switch from OSS to ALSA. That allowed multiple programs to use sound on my machine... YMMV

---

