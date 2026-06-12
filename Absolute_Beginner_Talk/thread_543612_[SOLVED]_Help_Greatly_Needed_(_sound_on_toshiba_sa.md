---
title: "[SOLVED] Help Greatly Needed :( sound on toshiba satellite not working"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-09-05
i need help getting my sound to install properly

i have this loud hiss and the volume is relatively low on it  i used the options snd-hda-intel model=3stack edit for my 
gedit /etc/modprobe.d/alsa-base

---

### Post by ThrobbingBrain66 on 2007-09-05
The good news is that you may not have to bother with all that :)

Open a terminal and type
```
gksudo gedit /etc/modprobe.d/alsa-base
```

At the end of the file, add the following line:
> options snd-hda-intel model=auto
After a reboot, you should have sound.  If not, try opening the same file and replacing 'auto' with '3stack' and reboot again.

---

### Post by Vic! on 2007-09-05
Loud hiss :( need help thanx your 3 stack option worked though im almost there

---

### Post by ThrobbingBrain66 on 2007-09-05
Type 'alsamixer' into a terminal and see if it allows you play with the volume settings and things.  Something like the microphone input could be turned way up and causing the hissing.

---

### Post by Vic! on 2007-09-05
Yep throbbing brain ur absolutely right... that was it mic imput was wayyyyyy up  .... thanx alot ! :)

---

