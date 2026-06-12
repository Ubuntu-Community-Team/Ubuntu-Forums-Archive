---
title: "Forcing sound through laptop speakers"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by ddalton on 2008-03-26
Hi,
I have just installed ubuntu 7.04 to my laptop.
The laptop doesn't have a pc speaker and some sounds seem to be going to that.
Like festival.
So how do I force all sound from alsa and os to go to the 
laptop speakers?
Not the pc speaker?
Sound in gnome seems to go to the laptop speakers, but sound in the console seems to go
to pc beeper.
How do I fix this?
Its possible that alsa could be doing what I want and os is the problem.
Anyway does anyone know how to fix this?

Thanks

---

### Post by ferdostar on 2008-03-26
Check if everything is OK in alsamixer 
```
alsamixer
```
Otherwise you can go to System -> Preferences -> Sound and choose the device and capture options you want.

---

