---
title: "Sound Works but.."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-01-08
I dont know if anyone else has had this problem but my sound quality and max volume suck on ubuntu (6.06 and 6.10). I have altec Lansing speakers built into the front of my laptop and on windows they work very well, good quality and able to get pretty loud. But on Ubuntu the sound doesnt get very loud and the quality is kinda crappy, even if I use headphones! Is there some kinda of driver I can change or setting I can tweak? I was thinking about maybe buying some external speakers, like one of the logitech speaker sets, would that fix the problem?

---

### Post by mahy on 2007-01-08
Sounds like a driver issue to me. What's your sound card? Have you tried some googling for soundcard-related issues and remedies?

---

### Post by oyvindaa on 2007-01-08
If you use ALSA, do this in the terminal:

```
sudo alsamixer
```

There you can up your volume.

---

