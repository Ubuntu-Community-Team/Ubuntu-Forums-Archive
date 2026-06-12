---
title: "SDL install?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by SoftTaco on 2006-09-05
Is there a way to get SDL from the repos?

---

### Post by mlind on 2006-09-06
> **SoftTaco said:**
> Is there a way to get SDL from the repos?

Do you mean libSDL package ?

---

### Post by jperez on 2006-09-09
That's what one of the teens I'm helping to install Ubuntu needs for Scorched 3D.  Ubuntu is asking for libSDL.  I've looked in plenty of places, but I can't find any gzipped packages or even DEB files.  How do you go about installing libSDL?  Thanks.

Jesse

---

### Post by mlind on 2006-09-09
This should do it
```

sudo aptitude install libsdl1.2debian-alsa

```

---

### Post by emprog on 2006-09-09
Enable multi/universe repos and do a search in synaptic for libsdl You need the dev packages and they are pretty much all there. Even many addon libraries like ttf, image and gfx

Erick

---

### Post by jperez on 2006-09-09
Thank you very much guys!  I learn new things everyday.  I'll be sure to save this for his computer.

Jesse~

---

