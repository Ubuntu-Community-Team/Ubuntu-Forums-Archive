---
title: "Still No Audio!!!  :("
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by G!zZm0 on 2008-02-10
I still dont have audio in my computer. This is frustrating me. I've tried everything but still no progress. My computer is a Dell Inspiron 1521. Maybe someone can help me get back my audio on my computer????

---

### Post by Jay Jay on 2008-02-10
I had this problem with Gutsy as well, try these commands in Terminal and see if they help restore your sound:

```
amixer set PCM 60 unmute
amixer set Master 60 unmute 
```

---

### Post by Majorix on 2008-02-10
^ You can do the same with alsamixer manually.

Also try "sudo alsaconf" and see if your driver was recognized.

---

### Post by G!zZm0 on 2008-02-10
It says:"No Such Device"...What should I do?

---

### Post by spiderbatdad on 2008-02-10
```
asoundconf list
asoundconf set-default-card Result
```where Result is the result of the first command. Reboot

---

### Post by Awperator on 2008-02-10
> **G!zZm0 said:**
> I still dont have audio in my computer. This is frustrating me. I've tried everything but still no progress. My computer is a Dell Inspiron 1521. Maybe someone can help me get back my audio on my computer????

Hello. I have an inspiron 1720, and this is what I used to get audio:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

Hope it helps

---

