---
title: "sound in x-windows applications"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by nikosft on 2006-05-28
Hi,

when I am running an x-windows that plyas sounds application such as videolan then any other x-windows application won't be able to play sounds. Why is that happening? It is really annoying!

Regrads
Nikos

---

### Post by nikosft on 2006-05-28
Oh I forgot, why also the filenames that ontain greek characters do not appear correctly?

---

### Post by CitizenKane on 2006-05-28
Some linux drivers for sound aren't able to do audio from more than one source at a time.  I am pretty sure that ALSA (Advanced Linux Sound Architecture) is able to.  If you are already using ALSA, it is possible that the driver for your sound card hasn't had support added for playing multiple audio sources at the same time.  I will poke around to see how to change this as I normally use KDE and not Gnome.

---

