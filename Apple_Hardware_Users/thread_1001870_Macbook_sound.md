---
title: "Macbook sound"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by vakyoomluigi on 2008-12-04
I've successfully triple-booted my macbook, with one problem:

The sound works in ubuntu, but it's not as loud or full-sounding as it is on mac.  Any suggestions on fixing this?

---

### Post by _mario_ on 2008-12-04
> **vakyoomluigi said:**
> I've successfully triple-booted my macbook, with one problem:

The sound works in ubuntu, but it's not as loud or full-sounding as it is on mac.  Any suggestions on fixing this?
in case you have a MacBook with Intel chipset (not the unibody ones), did you try adding:
```
# fix sound for SantaRosa MacBook(Pro)s
options snd_hda_intel model=mbp3

```
to /etc/modprobe.d/options?

ciao,
Mario

---

### Post by vakyoomluigi on 2008-12-04
aha! thank you very much:)

---

