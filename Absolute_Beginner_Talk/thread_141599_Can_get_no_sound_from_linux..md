---
title: "Can get no sound from linux."
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by billh1241 on 2006-03-08
Probably a simple thing but I can not get any audio from the computer.  I used the volume control...set up high...no sound.  Played a cd...no sound...played a dvd movie...no sound.  Please help.

---

### Post by 4dz0 on 2006-03-08
What version of ubuntu are you using?

---

### Post by Rumor on 2006-03-08
For me, it was as simple as clicking System -> Preferences -> Sound and selecting my soundcard as the default sound device. My Asus motherboard has integrated sound, and Ubuntu had defaulted to that device. As soon as I switched to the Audigy card, I had sound.

---

### Post by timsch75 on 2006-03-08
Try a different audio output under System-Preferences-Multimedia system selector.  I have ALSA installed and would use that, but can only get OSS to work.  Maybe you're in the same boat.  Other than that, type "alsamixer" at the command prompt and make sure all your mixer settings are right (if you're using ALSA).

---

