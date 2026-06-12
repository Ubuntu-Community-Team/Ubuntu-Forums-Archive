---
title: "Sound driver needed?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-04
Hello
I was attempting to install Ubuntu Gutsy on my friend's Acer Aspire 3682N. Maybe the model has a RealTek audio card. But I am not able to get sound in that. I have tried Restricted manager, which has nothing but an entry "HAL". Also, I tried different devices on the Sounds option including ALSA, OSS, Modem etc. but no use.. 
Any ideas?

---

### Post by kwacka on 2008-03-04
I would be very surprised if the soundcard is anything exotic.

First step, install something like gnome-alsa-mixer and make sure the 'external amplifier' box is cleared.

If that fails use 'lspci' to identify the card (AC97?)

---

