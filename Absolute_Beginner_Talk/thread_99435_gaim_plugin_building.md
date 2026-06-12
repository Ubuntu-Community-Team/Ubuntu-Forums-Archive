---
title: "gaim plugin building"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by ninjaPants on 2005-12-05
I'm trying to compile a couple of plugins for Gaim (extpreferences and guifications), but I keep getting this error when I run the configure script:

> 
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


I'm at a loss... I'm pretty sure I understand what it's telling me, but not what I should do about it.

I've got the full config log, but didn't post it here so I don't flood. If you need/want it, PM me. 

TIA

---

### Post by endersshadow on 2005-12-05
Easier way:

```
sudo apt-get install gaim-extpreferences gaim-guifications
```

Run that command in the terminal, and you'll be all set.

I guarantee you that you'll have to add at least 10 packages for that all to work, since you don't have any devel packages.  Just easier to use apt-get.

---

### Post by ninjaPants on 2005-12-06
Thanks! I'd usually not reply, but just in case anyone else comes to this thread for the same answer, the extended preferences package is actually called gaim-extendedprefs. And all the plugins can be found in the Synaptic package manager.
Yay learning!

---

