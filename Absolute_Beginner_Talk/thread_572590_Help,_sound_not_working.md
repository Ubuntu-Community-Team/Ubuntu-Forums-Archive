---
title: "Help, sound not working"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-10-10
I have looked at the comprehensive sound probelm solution guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) but it is very outdated and so are the links. Anwway, I have tried installing the newest alsa drivers but that did not work. I also fiddled with the volume control but that didn't work either. Any ideas as to what I could do? BTW, I have an HDA Intel soundcard.

---

### Post by Daveth on 2007-10-10
have you looked at this 

[http://ubuntuforums.org/showthread.php?t=568463&highlight=hd+intel](http://ubuntuforums.org/showthread.php?t=568463&highlight=hd+intel)

---

### Post by intense.ego on 2007-10-10
My computer is a Lenovo (IBM) Thinkpad T60. Should it work with me as well?

---

### Post by intense.ego on 2007-10-11
anyone?

---

### Post by aktiwers on 2007-10-11
I know how to fix this.. I did it the other day..
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Just download and compile the newest Alsa drivers and then update your 
/etc/modprobe.d/alsa-base  file.

Thats all. It looks like a lot, but really it isnt. :)

Good luck

---

### Post by intense.ego on 2007-10-11
I tried updating the alsa drivers but i don't think i updated the base file. I will try this when i have time and will get back to you.

---

