---
title: "problem :error while loading shared libraries"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by culback on 2006-04-05
hello I am a  beginner in linux and i have a problem when i try ti install a program
pl: error while loading shared libraries: libgmp.so.3: cannot open shared object file: No such file or directory
i don't know what to do 
thanks

---

### Post by mlind on 2006-04-05
hi, what program are you installing?

Are you building from sources or using apt-get? Prefer apt-get if your program is
available on apt repositories. Installing is as simple as running *sudo apt-get install yourprogram* from terminal.

Install synaptic to get graphical interface for apt.

You're probably after libgmp packages. try *apt-cache search libgmp*
to see what's available

---

### Post by culback on 2006-04-05
[QUOTE=mlind]



You're probably after libgmp packages. try *apt-cache search libgmp*
to see what's available[/QUOTE]

thank i just needed libgmp package

---

