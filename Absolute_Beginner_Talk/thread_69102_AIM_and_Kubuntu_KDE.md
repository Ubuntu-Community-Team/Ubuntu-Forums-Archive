---
title: "AIM and Kubuntu KDE"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by clueo8 on 2005-09-25
I installed aim for linux correctly in its place.  When I enter a terminal and type aim to run the program, i get:

aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Even then I'm in the install directory:

user@kubuntu:/usr/bin$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or direct

---

### Post by mlomker on 2005-09-25
Did you install **libstd++6-0**?

---

### Post by byen on 2005-09-26
yup looks like a dependency for the said file.
clueo8...this is what you do....click on System>add remove progs>advanced and use the search button to find  "libstdc" and right click on it to do an install... see if that works... if not let us know.  
And by the way...welcome to Ubuntu!!!

---

### Post by mcmillan on 2005-09-26
I'll add to the chorus of saying this is probably dependency problems. But also would like to ask if there's a reason you want to install AIM, considering GAIM should work just as well, and should be installed already.

---

### Post by clueo8 on 2005-09-27
I tried to go to the package installer in kde and download this lib file.  That did not help with AIM...

I'm really just learning and I know gaim or kopete will get me on with an AIM screen name, but I'm just upset that I couldn't get it to run!

---

### Post by mlomker on 2005-09-27
Sometimes there's no way to get something to compile....unless you're a programmer and can customize the source.  Compiling software is an advanced task.

---

