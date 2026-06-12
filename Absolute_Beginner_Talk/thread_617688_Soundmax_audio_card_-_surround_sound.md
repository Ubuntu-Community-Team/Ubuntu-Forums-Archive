---
title: "Soundmax audio card - surround sound"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by crammer2 on 2007-11-19
Hi I have an on board audio sound card (asus - M2N-E) - Soundmax is the driver, but i can't get Ubuntu to recognize it. I do have some sound two out of 6 speakers work- but no surround sound.Any ideas?

---

### Post by Pumalite on 2007-11-19
System>Preferences>Sound>Devices
See if you have Surround listed there.

---

### Post by crammer2 on 2007-11-19
It doesn't have surround listed there...

---

### Post by Pumalite on 2007-11-19
Post:
 sudo lshw -C sound

---

### Post by crammer2 on 2007-11-19
OK thanks surround is now there. Is there a configuration command to enable it? Right now only two speakers are working. Many thanks

---

### Post by crammer2 on 2007-11-19
Hey no worries I got it! I used the Alsamixer to enable the rest of the speakers. Thanks so much again!!

---

### Post by maxquiere on 2007-11-22
hi,

i have the same mainboard and  sound onboard..

i have done the same steps and commands but i cant get it working -.-

can you tell me what you've done to enable surround?

what means surround listed?

in system->settings->audio-> at the bottom there?

---

