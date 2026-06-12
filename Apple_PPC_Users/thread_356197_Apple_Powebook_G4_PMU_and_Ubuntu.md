---
title: "Apple Powebook G4 PMU and Ubuntu"
date: 2007-02-08
forum: Apple PPC Users
---

### Post by Nik_Doof on 2007-02-08
I've been trying for two days now and i've been unable to make my PB sleep on close lid events or even trying to force it via commands.

I initally installed pmud which didn't do much, then switched to pbbuttonsd to get support for various other events on my pb. The daemon is running and i've tried using "pbbcmd sleep" to force sleeping but it has no affect.

Does anyone have a guide on how to get this working?

---

### Post by Nik_Doof on 2007-02-08
Found my answer already, should of searched better.

Turns out that Nvidia based hardware cant suspend to RAM

[Thread](http://www.ubuntuforums.org/showthread.php?t=318310)

---

