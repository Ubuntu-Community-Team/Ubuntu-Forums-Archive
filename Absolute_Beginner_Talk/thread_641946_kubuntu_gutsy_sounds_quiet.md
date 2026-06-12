---
title: "kubuntu gutsy sounds quiet"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by p-real on 2007-12-16
i have a toshiba satalite sk9 a100 and im using gutsy gibbon sound is very quiet. turned all the way up on master vol and vlc

---

### Post by MangasColoradas on 2007-12-16
I have Ubuntu and had the same problem. Right click the volume icon and select volume control, turn up 'PCM'.

---

### Post by Capricori on 2007-12-16
Maybe a dumb question, but did you check alsamixer? (type alsamixer into a terminal)

---

### Post by p-real on 2007-12-16
> **Capricori said:**
> Maybe a dumb question, but did you check alsamixer? (type alsamixer into a terminal)

i typed sudo apt-get alsamixer into terminal i go E; couldn't find package

---

### Post by p-real on 2007-12-16
ok pcm at full figured it out me dumb still quiet tho!

---

### Post by Capricori on 2007-12-16
I thought it was there by default? If not, you might have to install the alsa-utils package.

---

### Post by p-real on 2007-12-16
u are right it was i was just impatient i figured out where it was my pcm is at full tho and its still quiet

---

### Post by sstusick on 2007-12-16
My Ubuntu Gutsy sound is very quiet also, the sound is like 1/4 the volume it should be. Everything is turned up in the alsa mixer.

---

### Post by discoade on 2007-12-16
Mine seams quiet to if i forget to alter the volume on the speakers and boot into xp it scares the hell out of me when the xp start music plays! :lolflag:

---

### Post by sstusick on 2007-12-16
Seems like a lot of us are having this problem...which sound cards do you have? 

I have a * 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)*

---

