---
title: "&quot;502 Bad Gateway&quot;?????"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by tsav87 on 2007-01-11
I was trying to add a program from "Add/Remove..." and I get this error on the screen.  Running Ubuntu v6.06 LTS.  How do I fix it?

-Travis

---

### Post by Albi on 2007-01-11
ok what you do is

sudo gedit /etc/apt/sources.list

and remove the us. in front of the repositories (so the first one in ur screenshot starts with [http://archive](http://archive))

---

### Post by Loki57701 on 2007-01-11
i have the same problem with the 502 bad bad gatway error. But why would this happen. Ive been updating my system just fine up until now.

---

### Post by Albi on 2007-01-11
I'm not sure actually, but tauros gave you the same advice.  My guess is that the us repositories are down at the moment so you'll just have to use the general ones, but as I said, I'm not sure.

---

### Post by tsav87 on 2007-01-11
Hey thanks, worked like a charm.

What do you think causesed it?

---

