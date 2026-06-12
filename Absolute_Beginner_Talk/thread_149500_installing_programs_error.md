---
title: "installing programs error"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by sscoop on 2006-03-24
i have installed ubuntu v5.10 and the make and gcc packages using synaptic package manager. when i run ./configure in every program i get an error saying that the c compiler cannot create executables. are there aditional libraries needed. i only did the steps below on a newly formated hdd
1. install ubuntu 5.10
2. install gcc and make packages with synaptic package manager

---

### Post by harisund on 2006-03-24
I would suggest you try and install a program called "build-essential" through Synaptic, or easier still through the command line. This will give you more tools that are essential for building applications.

---

### Post by sscoop on 2006-03-24
thanks. it works now

---

### Post by celloandy on 2006-03-24
Ubuntu only includes the binary, pre-compiled libraries necessary to run programs, and not the source code needed to compile new ones.  If you want to compile your own programs, you'll need to install the necessary development packages.  You can use Synaptic (or apt-get or whatever) to install those packages.  Look for [name-of-library]-dev packages.

Out of curiosity, what are you trying to install?  It's likely that you'll be able to find pre-compiled packages, either in apt, or elsewhere, for these programs, and not have to worry about compiling things for yourself.

Andrew

---

