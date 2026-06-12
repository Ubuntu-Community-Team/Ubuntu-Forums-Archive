---
title: "no sound in ubuntu 7.10 after a couple restarts"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-10-23
i've recently installed ubuntu 7.10 and everything was working fine.. sound..video driver..network connection.. . I installed a couple of apps... and after one of'em i think i needed a restart..(i believe Limewire) and noticed that after that there was no sound. I tested all sound devices in System ->Preferences ->Sound and only one worked.. i thought "great! i fixed it".. but no.. still no sound, i tested it with youtube..or with the system sounds.
Anyway, i noticed that mp3 and other stuff in RythmBox work. I can "hear" the music, but nothing else.. no system sounds ( they are not turned off.. not that dumb :P ) . I need my youtube also :D.

What to do?

i have an Nvidia Nforce2 sound card
thanks

---

### Post by panti19 on 2007-10-23
wow.. another restart and the sound miraculously works.
but i don't know if i do another it will again.. :(

---

### Post by Nick Fedchik on 2007-10-23
I had the problem like You.
Use 'alsamixer' and set up both Master and PCM channels to the values more than zero.

---

### Post by panti19 on 2007-10-24
still doesn't work...
help :confused:

---

### Post by panti19 on 2007-10-24
when i right click the volume control and click preferences , i have a choice of 3 devices:

CA0106 (Alsa Mixer)
Nvidia Nforce2 (Alsa Mixer)
mixer00 (OSS Mixer)



i believe that CA0106 is my second audio card (Creative SoundBLaster X-FI) but i know it is not supported and i must use the onboard one.
it worked after i installed ubuntu.. but after a couple restarts it stopped, but only "multimedia sound" plays..
mp3s, videos.. 
not system sounds or any other app sound

:confused:

---

### Post by panti19 on 2007-10-24
anyone?
bump..

---

