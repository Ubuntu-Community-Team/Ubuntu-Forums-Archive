---
title: "Audio always boots up at the lowest level"
date: 2006-06-11
forum: Apple PPC Users
---

### Post by humina on 2006-06-11
Every time that I boot my computer The audio is at the lowest level.  I have to hit the audio up keys about 5 times every single time I boot.  How can I have the audio on my ibook G4 boot with a predetermined level?

---

### Post by bluemonki on 2006-06-12
If you're using the ALSA drivers, set the level then in a console do:

# sudo alsoctrl store

You might need to install some alsa utils to get alsaconf and alsactrl

Hope that helps

---

