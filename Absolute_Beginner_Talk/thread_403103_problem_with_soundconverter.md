---
title: "problem with soundconverter"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-06
I have installed "soundconverter" with Synaptic PM but under format's mp3 is grey and i can't select it, why o why?

---

### Post by zvacet on 2007-04-06
Do you have codecs to play mp3?
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by cele on 2007-04-06
nope! Second day user. I just started to read [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
so I will figure it out soon.

---

### Post by cele on 2007-04-06
I installed
gstreamer0.10-ffmpeg & gstreamer0.10-fluendo-mp3
and still nothing. Did i miss something?

---

### Post by cele on 2007-04-06
I have fixed the problem. 
"gstreamer0.10-plugins-ugly-multiverse" was missing.

---

### Post by zvacet on 2007-04-06
Install win32 codecs too.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

