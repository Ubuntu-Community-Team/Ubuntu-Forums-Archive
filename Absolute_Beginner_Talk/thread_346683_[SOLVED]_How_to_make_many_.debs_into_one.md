---
title: "[SOLVED] How to make many .debs into one"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-01-26
Hi , I have given Ubuntu to many of my friends and they really like it but they do not have an internet connection or DVD ROM and they need to install support for audio and other packages. So ive committed to give them those packages on CDs. But here starts the problem , i went to packages.ubuntu.com and downloaded .debs for all the plugins needed for playing sound files and video files but when i tried to install them they said missing dependencies so i downloaded those dependencies too but some of them weredependant on other dependencies (LOL) so its a big headache to click 40 debs and keep clicking install package install package install package...SO is there a way by which i cud place all the .debs in a folder and it will resolve the missing dependencies using those .debs only.That would be fabulous!! Thanks

---

### Post by deadgobby on 2007-01-26
Instead of sudo apt-get. Try the super cow power of 
sudo aptitude install (file name) If you have the pack it may look for the depends.
Gobby

---

### Post by Jussi Kukkonen on 2007-01-26
You can put up a local Trivial Repository: [http://www.debian.org/doc/manuals/repository-howto/repository-howto#id2452849](http://www.debian.org/doc/manuals/repository-howto/repository-howto#id2452849)

But, In the end wouldn't it be easier to just to ***sudo dpkg -i *.deb*** in the correct directory?

As for the dependency problem, try installing the wanted package with ***sudo apt-get install --simulate packagename***, that should print out a list of the dependent packages ...

---

### Post by ashmew2 on 2007-02-01
Thanks!! The sudo dpkg -i *.deb did the trick , some packages failed due to missing dependencies first time but then when i ran that command second time it worked cuz dependencies were installed in first time :D Thanks

---

### Post by Muffe on 2007-02-01
> **deadgobby said:**
> Instead of sudo apt-get. Try the super cow power of 
sudo aptitude install (file name) If you have the pack it may look for the ```

```depends.
Gobby

Remember, aptitude does **not** have super-cow capabilities!

Source (aptitude -h):
```
(...)
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
```

Just to clear things up a bit...

---

### Post by ashmew2 on 2007-02-18
what does cow powers mean?

---

### Post by mcduck on 2007-02-18
> **ashmew2 said:**
> what does cow powers mean?

that's just a joke :) Try 'apt-get moo' and you'll understand..

---

### Post by ashmew2 on 2007-02-18
lolololo!! and in aptitude moo it says "NO EASTER EGGS"
roflmao

---

### Post by mcduck on 2007-02-18
> **ashmew2 said:**
> lolololo!! and in aptitude moo it says "NO EASTER EGGS"
roflmao

It's telling you lies.. try 'aptitude moo -v'. And then 'aptitude moo -v -v'. and keep on adding more of the '-v' and you'll see.. ;)

---

### Post by kinematic on 2007-02-18
another great one is > apropos women
linux is definiteley a guy invention lol.

---

### Post by ashmew2 on 2007-02-18
roflmfao LOL!! The people that made the base of ubuntu sure were funny......and guys lmao

---

