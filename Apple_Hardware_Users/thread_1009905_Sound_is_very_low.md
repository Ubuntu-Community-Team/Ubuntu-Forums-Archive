---
title: "Sound is very low"
date: 2008-12-13
forum: Apple Hardware Users
---

### Post by blippy on 2008-12-13
Hi, I've put Ibex on my Mactel. The sound is very quiet, despite the fact that I have the volume meter on the gnome panel and Totem turned up to the max. If I play Aesop's Fables, for example, the volume is very low. It's a problem with all audio files. Sound is not a problem in OS X.

Any ideas?

---

### Post by blippy on 2008-12-13
> **blippy said:**
> Hi, I've put Ibex on my Mactel. The sound is very quiet, despite the fact that I have the volume meter on the gnome panel and Totem turned up to the max. 

I installed Gnome Alsa Mixer, started it, and moved the Front and PCM volume control to maximum. That helps.

---

### Post by logos34 on 2008-12-13
yeah, the separate PCM volume level causes more confusion

---

### Post by Rog-Mahal on 2008-12-13
I've also found that keeping the volume level in OS X around 40-50% and then rebooting into Ubuntu also makes a difference. Making it higher than that can produce an annoying crackling sound in the left speaker.

---

### Post by logos34 on 2008-12-13
> **Rog-Mahal said:**
> I've also found that keeping the volume level in OS X around 40-50% and then rebooting into Ubuntu also makes a difference. Making it higher than that can produce an annoying crackling sound in the left speaker.

+1

a lot of complaints about crackling/distortion could be solved by simply lowering the PCM level from max (the threshold on mine is 84% before I start getting noise on the higher freqs/pitches)

---

