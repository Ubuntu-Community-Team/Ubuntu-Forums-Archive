---
title: "Making Ubuntu read .exe files?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Dexter1337 on 2007-07-28
Can some one teach me or point me in the derection to make Ubuntu support .exe files?

---

### Post by scotty32 on 2007-07-28
install Wine with Synapitc

look at [www.winehq.org](www.winehq.org)

---

### Post by Lycaon on 2007-07-28
Hello Dexter1337,

*nix systems do not support the exe structure, and can't be run.
However there are ways of emulating them, Wine is the solution for that. (see scotty32's post).
Here is a link that would help you setup wine up and running in a few minutes:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Install_Wine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Install_Wine)

But if you know the executable is a .net compiled exe, you could run it with mono.

sudo apt-get install mono
mono <your exe>

hope i didnt miss any points:) have fun

---

### Post by Dexter1337 on 2007-07-28
Thanks guys!

kthnxbai

---

### Post by mkoehler on 2007-07-28
A quick disclaimer about Wine:

- Not *all* programs will run with wine, even if you install them through wine.
- Most programs won't work *unless* you install them through wine.

Basically, what I'm saying is that you should run the install executable through wine and the program *should* run properly, but no guarantees.

Good luck!

---

### Post by hessiess on 2007-07-28
i have only managed to run programs that do not need installing on wine

---

### Post by buddah3618 on 2007-08-15
Hi

I just installed a program through " Wine " & it appears to be working just fine.

Thanks for the Info
buddah3618  :)

---

