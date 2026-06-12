---
title: "No System sound"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-12-04
In GUTSY I can't get the system sound working through my USB Logitech speakers or Headphone but I can listen to sounds and videos with no problem.
If I use my 3.5mm jack Headphone I am able to hear the system sounds
I have Realtek ALC883, may be I didn't set the sounds preferences properly.
THANKS.

---

### Post by frodon on 2007-12-04
Run this command :
```
sudo apt-get install esound
```It will install the esound system which handle system sounds, this problem has been reported by many users with gutsy so the fix should work for you too.

---

### Post by jmfa59 on 2007-12-04
It is already installed

---

### Post by frodon on 2007-12-04
Then check your audio settings, the correspondind channel may just be muted. You may have to go in preference in the sound setting window to be able to see more channels and see the one who is muted and shouldn't be.

---

