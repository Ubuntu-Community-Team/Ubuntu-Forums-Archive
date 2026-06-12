---
title: "I'm getting frustrated with the sound card!"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-03-03
No matter what I do I cannot get Ubuntu to switch the defaut sound card. Please help me I use the command sudo asoundconf set-default-CMI8783MC8 and not matter what the onboard sound card always stays default.:mad::confused:

 Please help me

---

### Post by psam3 on 2008-03-03
Well I got it to give me sound out of one of the soundcards but now I can't control the volume from the thing on the taskbar. I have to use alsamixer to control volume. How can I restore control to the volume bar on the taskbar?

---

### Post by happyhamster on 2008-03-03
> **psam3 said:**
> Well I got it to give me sound out of one of the soundcards
Does that mean it all works as it should now? If not, try disabling onboard sound in the bios first. If that doesn't help, could you show the output of the following commands:

aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base
cat ~/.asoundrc.asoundconf

They give detailed info about your sound hardware and configuration.

>  but now I can't control the volume from the thing on the taskbar. I have to use alsamixer to control volume. How can I restore control to the volume bar on the taskbar?
Right-click the volume icon on your panel and choose Preferences. In the lower window are all available sound channels listed (Master, Headphone, PCM, etc). The one you select here, will be the channel controlled by the volume slider. So just keep trying until you find the one you want to use.

Good luck, and keep us informed.

---

