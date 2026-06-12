---
title: "no acceptable C compiler found"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by essendon on 2005-07-16
Hi there.

When I run ./configure for xmms I get this error:

configure: error: no acceptable C compiler found in $PATH

What am I doing wrong?

---

### Post by RastaMahata on 2005-07-16
[QUOTE=essendon]Hi there.

When I run ./configure for xmms I get this error:

configure: error: no acceptable C compiler found in $PATH

What am I doing wrong?[/QUOTE]
 have you installed build-essential?
```
sudo apt-get install build-essential
```

---

### Post by SGC on 2005-07-16
xmms is in the ubuntu repositories, there is no need to compile it, just run:
```
sudo apt-get install xmms
```

Or search for it in synaptic

---

### Post by essendon on 2005-07-20
Have fixed it.  Thanx for the advise.

---

