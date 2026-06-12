---
title: "Permission Problem."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-21
I have just tried to run in the root terminal   /etc/apt/sources.list  and got permission denied. Do I have another problem?

---

### Post by torgrot on 2008-01-21
Did you enter this ```

gksudo gedit /etc/apt/sources.list

```
into a terminal.  It will prompt you for your password and then let you edit the file and most importantly save it.

torgrot

---

### Post by newbeeman on 2008-01-23
> **torgrot said:**
> Did you enter this ```

gksudo gedit /etc/apt/sources.list

```
into a terminal.  It will prompt you for your password and then let you edit the file and most importantly save it.
torgrot

I forgot what i was doing and jumped in. The previous post answer gave a command /etc/apt/sources which I ran and got an error. I was using the root terminal which I believe was wrong?

---

