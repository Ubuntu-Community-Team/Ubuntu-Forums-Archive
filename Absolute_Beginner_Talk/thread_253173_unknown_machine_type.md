---
title: "unknown machine type?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-09-07
I built  new computer, and the very first thing I did was install Ubuntu 6.06 LTS. The computer is 3400+ AMD 64 on a MSI motherboard.

Now I'm trying to compile some library's so I can compile a few games and I get this:
./configure
checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
configure: error: /bin/sh ./config.sub x86_64-unknown-linux-gnu failed

What now? :-)

---

### Post by orb9220 on 2006-09-07
Did you install the 32-bit or 64-bit kernel on your machine?

---

### Post by jordanmthomas on 2006-09-07
*[COLOR="DimGray"]Did you install the 32-bit or 64-bit kernel on your machine?[/COLOR]*

You can find out by typing this on a command line:
```
uname -r
```

---

