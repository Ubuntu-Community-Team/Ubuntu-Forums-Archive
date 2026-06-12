---
title: "SMC and Supertux"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by skrribble on 2007-12-17
I have installed supertux and smc (Secret Maryo Chronicles) but neither seems to work... Heres what I get in a terminal:
```
~$ smc
Error : SDL initialization failed
Reason : No available video device

```
for supertux i get:
```
~$ supertux
[/home/jacob/.supertux2] is in the search path
[/usr/share/games/supertux] is in the search path
Fatal: Unexpected exception: Couldn't initialize SDL: No available video device
```
i have no clue what those are about... just for info, i have ati mobility x600 using the proprietary driver with compiz disabled, if that matters

---

### Post by jinx099 on 2007-12-17
Did you install supertux from the repos?  Make sure you have all the SDL stuff installed, that's probably the issue.

---

### Post by skrribble on 2007-12-17
i have everything that i can tell has anything to do with sdl installed.... all of the packages that start with libsdl and cl-sdl and the bindings for sdl.... is there anything else to install???

i think i got everything, but they still wont work

---

