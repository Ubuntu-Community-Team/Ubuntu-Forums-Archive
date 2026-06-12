---
title: "Crappy Sound"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by shawnhcorey on 2006-10-20
I have a PowerBook G4 running Gnome under 6.06LTS. The sound from my CDs is really crappy. I tried Sound Juicer and CD Player. CD Player is slightly better. The sound from Totem-xine is even better but not what you'd expect for digital sound. I even tried playing arround with alsamixer but no luck.

Any suggestions?

---

### Post by calum on 2006-10-24
What did you change in alsamixer?  It's not uncommon to have to adjust to adjust the PCM levels there on PPC Macs (either downwards to avoid distortion, or upwards to get any kind of sound at all).

---

### Post by shawnhcorey on 2006-10-24
Yes, I got a hold of the ALSA mailing list and discovered that PCM is the first digital channel (and PCM 1 is the second). By lowering its value I was able to avoid the worst of it. But I still haven't figured out the best value for it.

They also said that the problem was in the sound driver or the chip. Since I don't want to send hundreds of hours trying to figure out how best to change the software, I guess I'll have to live with it.

I still haven't figured out what DRC stands for, why there is a control for it, and what DRC Range does. Sigh. :-?

---

