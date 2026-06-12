---
title: "stupid newbie question"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by teqsun on 2008-04-10
I am running Ubuntu Server  and I am wondering if there is a way to check my ram from the terminal.

---

### Post by Tatty on 2008-04-10
Try...
```
free
```

Be aware that linux attempts to use all available memory all the time, so it will probably appear to be full.  You need to take into account the second line "cache", which says how much space can be cleared if you load something else.

---

### Post by Jason2gs on 2008-04-10
You mean, your current RAM usage?

Try running 'free'.

(Note, this is tested on the Ubuntu Desktop edition. Not the server edition.)

---

### Post by teqsun on 2008-04-10
Thanks all, that was exactly what i needed.

---

