---
title: "Problem with compiling with gcc"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2006-10-04
Hi,

I've got small c program. I've installed gcc-3.3 (I've compiled this app before on my friends system using this version), gcc-3.3-base and even docs package, but it keeps complaining about missing basic header files like stdio.h etc. Do I need to install something else or reinstall these packages?

[EDIT] Sorry for trouble, I've just found out that I need libc6-dev package.

---

### Post by davmac on 2006-10-04
The easiest way I've found of gettiong this set up is to install "build-essential", this gets you most of the stuff you need.

Dave Mac

---

### Post by Sef on 2006-10-04
To install build-essential:

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install build-essential

---

