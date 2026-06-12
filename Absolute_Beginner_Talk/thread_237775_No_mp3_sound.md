---
title: "No mp3 sound?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-08-16
I was playing MP3s just fine for the past few days. Today I pressed play and no sound. Amorak said something about "sound device in use". However, sound works fine in video and flash objects. 

Any idea what could be causing this ?

---

### Post by deadgobby on 2006-08-16
open up the terminal and type in .

killall esd

See if that helps
Gobby

---

### Post by ComplexNumber on 2006-08-16
> **deadgobby said:**
> open up the terminal and type in .

killall esd

See if that helps
Gobby
i agree.

---

### Post by toykilla on 2006-08-16
Cool that worked. What is esd ?

---

### Post by ComplexNumber on 2006-08-16
> **toykilla said:**
> Cool that worked. What is esd ?
the enlightenment sound daemon. traditionally, its been the gnome sound server.

---

