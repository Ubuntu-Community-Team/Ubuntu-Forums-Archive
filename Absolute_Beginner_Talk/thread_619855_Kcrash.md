---
title: "Kcrash"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-11-21
I am posting in behalf of my sister, and she is having a unusual problem, so she tells me.
She says that her Gimp and Tellico will crash when she clicks the save button, so I test it, and Gimp doesn't crash on me, yet Tellico does.

I ran it through the terminal, and here is the error code that it spit out when it crashed:
```
KCrash: Application 'tellico' crashing...
KCrash cannot reach kdeinit, launching directly.

```

Any idea about this ? I know nothing about KDE or how it works. She is running Gnome, but apparently Tellico is a KDE application or something.

Any help would be appreciated.

Dr Small

---

### Post by wieman01 on 2007-11-22
Could it be that her /home partition is running low on space?

---

### Post by Dr Small on 2007-11-22
> **wieman01 said:**
> Could it be that her /home partition is running low on space?
She doesn't have a /home partition, so that wouldn't be the problem.
I think it looks like some kdelib is missing or something, but I don't know what.

I have tried removing tellico with --purge and reinstalling, but it made no effect.
Thanks for your response.

Dr Small

---

### Post by Dr Small on 2007-11-22
Also, I found out that it doesn't seem to do it while running telico as gksudo, so I don't know if that would be any helpful and strike an inspiration!

---

