---
title: "WINE help"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by fitzybhoy on 2007-11-06
guys, i need some help with some applications using WINE.

when i try to install football manager, the screen pops up but disappears very quickly. i cant get it installed. i have the official disc and have wine configured for windows 2000, then windows XP for the installation (guide from this forum)

also, i cant get windows live messenger working using it.

any help?

---

### Post by skymera on 2007-11-06
windows live messenger?

[www.amsn-project.org](www.amsn-project.org)

near enough the same when you fiddle with it.

which wine version are you using?

---

### Post by fitzybhoy on 2007-11-06
> **skymera said:**
> windows live messenger?

[www.amsn-project.org](www.amsn-project.org)

near enough the same when you fiddle with it.

which wine version are you using?

i've downloaded that AMSN thing.

how do you install it?

---

### Post by PmDematagoda on 2007-11-06
You don't need to download it and install, it is there in the repos, simply type:-
```

sudo apt-get install amsn
```

and you will install aMSN.

---

### Post by rudeboyskunk on 2007-11-06
As for the Football Manager, try to install it from command line.  Open a terminal, cd to the installation directory, and type "wine setup.exe" (or install.exe, or whatever the installation file is called).  If it still crashes, copy and paste the output from the terminal in here.

It might be crashing because you have your sound set to ALSA.  Under your Wine Config GUI, see if changing it to OSS works.

---

