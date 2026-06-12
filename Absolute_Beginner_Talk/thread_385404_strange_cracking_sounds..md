---
title: "strange cracking sounds."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-15
yes the title says it all... certain programs such as zsnes and sound recorder and also certain games such as emilia pinball and even sometimes certain .mp3s have strange cracking and buzzling sounds. i remember i had this issue on windows too and had to edit somthing. i have a intel 82801DB-ICH4 sound card. how can i fix this sound problem?

---

### Post by thingy on 2007-03-15
hmm

Could be that the PCM mixer value is set too high. Run alsamixer and set the PCM value to be about 70% i.e. not red. Use the master mixer to go as high as you want but leave the PCM at 70% ish.

---

### Post by noob_saioke45601 on 2007-03-15
thanks but where can i find the alamixer? is it installed by default or you have to install it through package manager?

---

### Post by thingy on 2007-03-15
its alsamixer and its prob. in alsa-tools or alsa-utils

try sudo apt-get alsa-tools
or sudo apt-get alsa-utils

---

### Post by noob_saioke45601 on 2007-03-15
ok lowered the pcm and still buzzing and cracking :(

---

### Post by thingy on 2007-03-15
If you had this issue on windows...you need to tell us what you did to fix it, since im at a loss to suggest other things. i mean, there are things you can rule out, like the kernel, applications running etc. but i dont want to suggest those until we find out what happened in windows.

---

### Post by noob_saioke45601 on 2007-03-15
ok here's what i did with windows.

1. opened control panel
2. clicked sounds, then speech, then audio devices.
3. clicked the sounds and audio icon
4. clicked the advanced button (or tab i cant remember)
5. a window pops up then you click on the performance tab.
6. moved the slider all the way to the left (the slider under hardware acceleration.


then the sound acted normal. any ideas?

---

