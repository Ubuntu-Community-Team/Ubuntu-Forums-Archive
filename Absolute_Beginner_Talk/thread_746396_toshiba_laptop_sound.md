---
title: "toshiba laptop sound"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by marmac2002 on 2008-04-05
there is a line that I need to add to the end of the file found in the 
etc/modprobe-d/alsa-base.
if anyone can tell me what it is I will get my sound working.
thank you

---

### Post by stomakmonkee on 2008-04-05
Some Satellites require this line to the /etc/modprobe.d/alsa-base --

options snd-hda-intel model=lenovo

Hope this helps.

---

