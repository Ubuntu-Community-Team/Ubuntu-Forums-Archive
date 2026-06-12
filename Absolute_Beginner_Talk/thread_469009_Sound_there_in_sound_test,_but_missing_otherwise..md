---
title: "Sound there in sound test, but missing otherwise."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-06-09
For some reason, I'm not getting any sound today. I booted up Ubuntu, and there's no sound anywhere. I went to the Sound options and I tested each of the devices, and they were working. But over at System Sounds, none is working. VLC player is not giving any sound either. Weirdest thing is, it just happened out of the blue. I tried going to .15, but there's nothing there either.

Again, sound is there is in the Sound Test, but nowhere else. What could be the reason?

---

### Post by Bohlio on 2007-06-09
This happened to me upon installing kernel 16. What i did to fix it was, Go into 15 (cause 16 sucked :-P) and go into the sound options. I had to take all the options off of autodetect and set it on the card that i use. If that doesn't work for you, I dont know what to do then. Also, The sounds that ubuntu makes when you log in and start up didnt work for me after 16, so i had to go to the BIOS and disable my integrated sound card. Hope i helped :-)

---

### Post by Sabretooth on 2007-06-10
Actually, I'm not getting sound in either of the versions. My PC is an XP/Ubu dual-boot and XP is working perfectly fine. I'm starting to get irritated.

---

### Post by just learning on 2007-06-10
maybe check that your program(vlc) is set to your audio settings. also check that your sound control is set to your sound card.double click on the sound icon then file and change device.
i'm using kernel 16 and i have had no problems. i did however had lots of prob. when i first installed, with the sound.

---

### Post by Sabretooth on 2007-06-11
Taking some advice from [this thread,](http://ubuntuforums.org/showthread.php?t=463921) I found out that Ubuntu is not detecting my sound card itself! I have a Creative Vibra 128, but Ubuntu detects it as "CS4281 - Cirrus Logic CS4281". Any ideas where I can get drivers for my card? I can't find them anywhere via Google. Are any alternate drivers or anything?

---

