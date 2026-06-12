---
title: "No file ./configure"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2007-02-28
I finally decided to try compiling some programs from source, read all howtos/tutorials & even have a couple printed.  Downloaded the required/suggested tools:
build-essential
libgtk2.0-dev
checkinstall
linux-headers-`uname -r`
autotools-dev
hubackup

Went to compile 1st program, cd'd to directory[had ckd that necessary were present] ran code:   "./configure"  get error:  "no such file or directory exists"  did a search & it doesn't.  What am I missing???  Or what did I do wrong???

---

### Post by Adramelech on 2007-02-28
What appears on the directory?

---

### Post by energiya on 2007-02-28
What is the program you want to compile? See if there is a README or INSTALL in the folder. You should get the install instructions there. Not all programs compile & install with the "./configure. make, make install" scheme.

---

### Post by randiroo76073 on 2007-02-28
What I did wrong!  Was assume that configure, make, make install were part of the compile programs that I installed, not so, they are part of the source files[if thats what method the program uses to compile].  After pouring over several downloaded sources files the lightbulb came on, now that's what I call a "DUH-O" on my part, never "assume" cause we all know where that leads :)

Thanks for pulling my string energiya!

---

