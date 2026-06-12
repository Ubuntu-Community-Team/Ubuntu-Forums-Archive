---
title: "Default install folder?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by neo_weapon on 2007-08-31
I'm running edgy and just installed xmms. I want to know where xmms install into so i can go into that folder and make that my default app for streaming music on shoutcast. In general, I'm wondering if there is a default installation folder ubuntu uses similar to "Programs and Files" on windows. Thanks for your time.

---

### Post by felicity on 2007-08-31
you can

```
sudo updatedb
```

then

```
locate xmms
```

to find the binary file, but it should be in /usr/bin or /usr/share/bin

---

### Post by neo_weapon on 2007-08-31
thank you, that solves the problem.

---

