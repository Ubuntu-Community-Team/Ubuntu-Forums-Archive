---
title: "xgl help, compiz command problems"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-07
hey im having problems with xgl on my laptop.. i get to the part where you type compiz --replace gconf decoration etc etc etc...

i get a problem about a file not found libgl or along those lines, im guessing its an open gl problem

i installed the drivers for my card ati xpress 200m from the ati website, and its in my xorg.conf as fglrx for my driver

any idea's on how to fix that compiz step?
oh yeah, and im running the 64bit version of dapper

---

### Post by joshrobinson on 2006-05-07
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

:-(

---

### Post by adam.tropics on 2006-05-08
Hey, I have the same ridiculous ati card!! It does work just fine with Xgl/Compiz, though it takes a little coaxing!

Try [method 2 here]("http://compiz.net/viewtopic.php?id=389") involving the startxgl, and startcompiz scripts, and make sure you are using the fglrx from restricted modules, not from creating your own ati packages. It doesn't like them.

---

