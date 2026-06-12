---
title: "kiba installation"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by kaboom on 2006-11-12
hey all
i'm following this howto for installing kiba

[http://ubuntuforums.org/showthread.php?t=235643&highlight=kiba](http://ubuntuforums.org/showthread.php?t=235643&highlight=kiba)

when i get to step four: run the make command am i just supposed to type make into the directory?

if so i get this response:
kaboom@kaboom-laptop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.

thanks in advance for your advice

---

### Post by jordanmthomas on 2006-11-12
type in 
```
ls
```
and see if there is a makefile in there.

Also, try running 
```
./configure
``` before make

---

### Post by aidanr on 2006-11-12
theres a deb [here]("http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package"), would be easier unless you specifically want the latest cvs

---

### Post by jordanmthomas on 2006-11-12
I just downloaded the latest cvs and those instructions won't work for it.  There is no populate-dock.sh in the root directory.  It is now in the utils folder, and kiba-dock is in the dock folder.  Just look around in there and you should be able to find everything you need.

---

### Post by pianoboy3333 on 2006-11-15
> **aidanr said:**
> theres a deb [here]("http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package"), would be easier unless you specifically want the latest cvs

Where could I get the latest source?

---

### Post by jordanmthomas on 2006-11-15
```
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
```

---

