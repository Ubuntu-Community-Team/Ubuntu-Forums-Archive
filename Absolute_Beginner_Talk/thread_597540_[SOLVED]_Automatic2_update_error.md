---
title: "[SOLVED] Automatic2 update error"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by drawman on 2007-10-30
Probably very simple, but I'm very new at this:

> E: tzdata: subprocess post-installation script returned error exit status 10

E: util-linux: dependency problems - leaving unconfigured

I will try and learn to solve for myself, I've got a book coming..."Running Linux, 4th ed."  It might help???

Thanks,

Drawman

---

### Post by aysiu on 2007-10-30
What are you trying to do?

---

### Post by drawman on 2007-10-30
> What are you trying to do?


I get this message when trying to update Automatic2.

---

### Post by aysiu on 2007-10-30
**Step 1**:
[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#editfile)

**Step 2**:
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get remove automatix2
sudo dpkg --configure -a
```

---

### Post by drawman on 2007-10-30
I'm running Automatics 2.0.5

Thanks for you assistance.  so much to learn, so little time.

Drawman

---

### Post by por100pre1 on 2007-10-30
If the tzdata issue persists read [this]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193").

---

### Post by drawman on 2007-10-31
I think I have upgraded Automatix2 to the latest ver.  Automatics 2.0.5, but the following error message stops all package installations and upgrades:

> E: tzdata: subprocess post-installation script returned error exit status 10

E: util-linux: dependency problems - leaving unconfigured

I will say that the Automatix2 problem is solved,  The tzdata issue persists...

---

