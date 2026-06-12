---
title: "C compiler"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by smallguy on 2006-05-04
I downloaded the source to a program I wanted to install
onto my ubuntu box, and there doesn't seem to be a C
compiler in ubuntu...

---

### Post by nanotube on 2006-05-04
from a terminal, run
```
sudo apt-get install build-essential
```
that will install the c compiler and a bunch of other build tools. don't know why they don't install it with the default install, but they don't, so ...

---

### Post by 3rdalbum on 2006-05-04
[QUOTE=nanotube]from a terminal, run
```
sudo apt-get install build-essential
```
that will install the c compiler and a bunch of other build tools. don't know why they don't install it with the default install, but they don't, so ...[/QUOTE]

The reason is: New users shouldn't try to compile software from source; it's sometimes a bit difficult, and always a little intimidating.

Smallguy: Have you tried looking for the program you want in the Synaptic Package Manager program? That should always be your first step. I know firsthand how, when new users want new software, they immediately go to the web - it's a learned behaviour from Windows and the Mac. I was like that a few months ago :p 

Good luck! (and don't forget, if you're compiling a program and it tells you that it needs special libraries, you can often get those from Synaptic as well)

---

