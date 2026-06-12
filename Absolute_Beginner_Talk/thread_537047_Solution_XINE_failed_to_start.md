---
title: "Solution: XINE failed to start"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ne0h on 2007-08-28
Those people getting this error "XINE engine failed to start" while trying to play DVD on XINE, here's is the solution. Just install ffmpeg plugin using following command.

```
aptitude install libxine1-ffmpeg
```

Thats it. Done.

---

### Post by gilf on 2008-05-01
Not quite.

```
sudo aptitude install libxine1-ffmpeg
```

---

