---
title: "Audio is gone"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-07-07
Here's my problem. Yesterday my audio worked great. I could listen to music in Banshee, no problem, got sound from intarwebs sites, the whole deal. I wake up today, and all of a sudden there is no sound on my laptop. The onboard sound (Realtek ALC883) is detected and appears to be working. What could my problem be? I have tried a different media player, and same situation no sound from either my Logitech Z4 speakers or the built in laptop speakers.

---

### Post by Pragmatist on 2007-07-07
Try using alsamixer to make sure all of the volume settings are unmuted and high enough.  Type this in a terminal:
```
alsamixer
```If you need to unmute a column (a column is muted if there is a MM on the bottom of it) you just press "M"

To increase the volume you use the up-arrow and to switch between columns, you use the left and right arrows.  When you are finished, just hit the "ESC" key.

---

### Post by amazingtaters on 2007-07-07
Problem was fixed with a reboot.

---

