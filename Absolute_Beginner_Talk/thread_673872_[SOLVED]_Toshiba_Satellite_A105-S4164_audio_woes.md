---
title: "[SOLVED] Toshiba Satellite A105-S4164 audio woes"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Helven Ink on 2008-01-21
Audio device:
Intel Corp. 82801G (ICH7 family) High definition Audio controller (rev 02)

I'd really like to fix the audio on my laptop... It's just so quiet... I can hardly hear anything with the volume turned all the way up...
Does anyone have any ideas about this?

         Jon

---

### Post by Helven Ink on 2008-01-21
bump

---

### Post by Helven Ink on 2008-01-21
bump

---

### Post by oodledoodle on 2008-01-21
go into terminal (applications > accessories > terminal) and type "alsamixer" without the quotes of course.
use the keyboard arrow keys to move across and make sure all your speakers are turned up properly. turning them up too high will result in distortion though, so bear that in mind

---

### Post by fedex1993 on 2008-01-21
i am guessing your sound is not working.Well i ahve a toshiba laptop and this is how i got my sound working.

Okay open up a terminal (accessories>Terminal) and type
```
sudo gedit /etc/modprobe.d/alsa-base
```
and then scroll all the way to the bottom of the text and instead
```
options snd-hda-intel position_fix=1 model=3stack
``` 
and then save the file reboot and yo should be amazed with sound.

Also bump every 24 hours

---

### Post by Helven Ink on 2008-01-21
Yay! I found something. SOund is working now!

---

### Post by Helven Ink on 2008-01-21
Thanks Oodlenoodle, and Fedex!
I found a thread on it and fixed it with:

sudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

I appreciate the help though! =) Now I just need to figure out my wifi...

---

