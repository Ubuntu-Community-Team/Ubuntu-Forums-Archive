---
title: "no sound card"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by JParkus on 2006-12-25
i just put ubuntu on my comptuter everything is working well exept one thing 
my sound linux has mot found my sound card i have a old p2 compaq

---

### Post by dbbolton on 2006-12-25
are you using alsa ?

---

### Post by xyz on 2006-12-25
See what gives when you run in a terminal:
```
sudo asoundconf list
```

---

### Post by JParkus on 2006-12-25
where do i go to enter commands

---

### Post by xyz on 2006-12-25
> **JParkus said:**
> where do i go to enter commands
OOps! Sorry I forgot!
Go Applications > Accessories > Terminal

This will open a terminal (a sort of window) with this already typed in:
> th@luser:~$
Of course you won't have 'th' nor 'luser' since these are mine.
Then copy this:
```
sudo asoundconf list
```
and paste it in the terminal.  Hit "Enter".Hope this is clearer.

---

