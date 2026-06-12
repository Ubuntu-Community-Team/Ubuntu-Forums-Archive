---
title: "how we can install ALSA in ubuntu"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-13
how we can install alsa by using synaptic packages.
because i my program i want  to include alsa/asoundlib.h so i want  to install alsa .
thank u,in advance
sree.

---

### Post by kostkon on 2007-08-13
Just go to Synaptic and search for *libasound2-dev*, select the package and install it; or, open a terminal and do:

```
sudo apt-get install libasound2-dev
```

---

### Post by wieman01 on 2007-08-13
Aeh... is it not installed by default? I am confused...

---

### Post by Spr0k3t on 2007-08-13
> **wieman01 said:**
> Aeh... is it not installed by default? I am confused...

I believe he is looking for the source files for ALSA which are not installed by default.

---

