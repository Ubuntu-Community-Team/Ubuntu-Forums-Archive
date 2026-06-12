---
title: "packages history"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-11-01
Does ubuntu keeps a track of the packages that have been installed, reinstalled or removed recently??

Thanks
Bruno

---

### Post by oldos2er on 2007-11-01
Yes.

---

### Post by Rui Pais on 2007-11-01
> **oldos2er said:**
> Yes.

One of the best answers i read so far :lol:

To my knowledge, there aren't a single log of all ways of installing...

Synaptic have its own way (under File->History)
apt keep a very complete log at /var/log/apt/term.log and aptitude at /var/log/aptitude.

---

### Post by twiceasworn on 2007-11-01
To see what packages you have installed do a 

```
aptitude search '~i'
```

---

