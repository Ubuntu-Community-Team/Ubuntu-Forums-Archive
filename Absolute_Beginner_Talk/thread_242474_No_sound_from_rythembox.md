---
title: "No sound from rythembox"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by schreck494 on 2006-08-23
This morning when I tried to play music in rythembox, there was no sound.  It showed the song playing.  I tried opening another player and it worked perfectly.  What could be wrong with rythembox?

---

### Post by anindya_m on 2006-08-23
By default rhythmbox uses esd as the sound output. Is your esd still running? Check with ```
ps aux | grep esd
```

---

### Post by schreck494 on 2006-08-23
It give me this:
> schreck   4910  0.0  0.9   5692  4132 ?        S    08:13   0:01 /usr/bin/esd -n obeeps
schreck  12515  0.0  0.1   2884   816 pts/0    S+   18:29   0:00 grep esd

---

