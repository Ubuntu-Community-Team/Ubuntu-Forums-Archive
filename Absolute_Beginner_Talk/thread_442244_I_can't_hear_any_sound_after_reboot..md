---
title: "I can't hear any sound after reboot."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by t.achim on 2007-05-13
Hi,
Suddenly sound has stopped working on my Edgy Eft system. I was watching a movie with kaffeine yesterday, then I shut down, and this morning I can't hear any sound from amarok or anywhere else.

How do I fix this?

---

### Post by gilgongo on 2007-05-13
It's possible that something has muted, or turned the volume down on alsamixer. Open a command line, type "alsamixer" (without the inverted commas) - shield your eyes from the resulting excuse for a user interface - and see if PCM is at anything less than 100, or if "Front" or "Surround" have an "MM" (mute) at the bottom. If the volume of PCM is low, raise it with the up arrow on the keyboard, if stuff is showing "MM" press the "m" key on the keyboard to unmute it.

---

### Post by bodhi.zazen on 2007-05-13
do you have more then 1 soundcard ? one on mother board + an additional ?

---

