---
title: "Turn off acceleration"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Auria on 2007-01-17
Hello everyone

i've found tons and tons of thread about how to get hardware acceleration to work, but couldn't find any clear information on how to completely disable it (found a few things i *think* might do it, but the information remained vague)

the rationale is that i'm getting all kinds of weird drawing artifacts in an OpenGL app, and it doesn't really require high performances.

---

### Post by Shatrat on 2007-01-17
What hardware do you have?
If you have nvidia for example, it is as easy as opening the /etc/X11/xorg.conf and in the Device section changing the driver from "nvidia" (nvidias binary-only driver) to "nv" (the freely distributable but limited one).
The ATI equivalents are "fglrx" to "ati" I believe, or maybe it's "radeon" I can't remember.

---

### Post by Auria on 2007-01-17
thanks all i wanted to know =)

---

