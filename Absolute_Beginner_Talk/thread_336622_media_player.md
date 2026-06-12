---
title: "media player?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by raminarya on 2007-01-11
I'm new to linux and just installed ubuntu. my media player can not play mp3, mov, or mpeg and i don't see any better player in the list of applications i can install. where do i find something?

appreciate your help,
raminarya

---

### Post by taurus on 2007-01-11
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Move to Beginner Talk.

---

### Post by raminarya on 2007-01-11
thank you very much. i have another related question: how can i read my windows CDs (with audio/video files) on my ubuntu pc?

cheers

---

### Post by taurus on 2007-01-11
Just pop it into the drive and see if it's automounted.

---

### Post by raminarya on 2007-01-12
thanx. it does work sometimes and not some other times. must be the way cd is made. 

appreciate your reply
ramin

---

### Post by Tomosaur on 2007-01-12
Some CDs are not technically CDs, and by law aren't allowed to carry the CD logo, since they contain stuff other than that required to play audio. My guess is the CDs which don't work automatically are those with no CD logo on them.

---

### Post by taurus on 2007-01-12
> **raminarya said:**
> thanx. it does work sometimes and not some other times. must be the way cd is made. 

appreciate your reply
ramin

If it doesn't mount automatically when you pop it into the drive, you can still mount it from a terminal though.

Applications -> Accessories -> Terminal
```
sudo mount /dev/hdc /media/cdrom0
(assuming your CD-ROM drive is /dev/hdc...)
```

---

### Post by raminarya on 2007-01-12
thank you very much

---

