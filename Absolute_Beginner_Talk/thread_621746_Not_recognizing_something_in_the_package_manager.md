---
title: "Not recognizing something in the package manager"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by MPChedda on 2007-11-24
I was busy trying to get the psx emulator installed, and something got a bit screwed up and now I get this message whenever I try to enter the synaptic package manager:

E: Type 'sudo' is not known on line 75 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Could anyone give me a hand? Much appreciated :D

---

### Post by rsambuca on 2007-11-24
You have an error in your sources.list  You can fix the 75th line by using a text editor called gedit.  To open the file in the text editor:```
gksudo gedit /etc/apt/sources.list
```

---

