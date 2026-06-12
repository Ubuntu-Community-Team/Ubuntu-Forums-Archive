---
title: "Alsa restart"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by InfernalPenguin on 2006-11-17
Im kinda a new to this and i have a simple question. What is a command to restart ALSA?

---

### Post by rouge568 on 2007-10-18
First try:
```
sudo /etc/init.d/alsa restart
```

And if that doesn't work, try:
```
sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]
```

I realize this is an old thread, but hey - it might help someone.

---

