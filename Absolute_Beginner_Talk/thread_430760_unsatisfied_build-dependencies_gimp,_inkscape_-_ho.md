---
title: "unsatisfied build-dependencies gimp, inkscape - how to get more info"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by BramKuijper on 2007-05-02
Hi all,

I am trying to build inkscape and gimp from source, so beforehand I execute:

sudo apt-get update;
works fine.
sudo apt-get upgrade;
works fine.

then I try to get all the dependencies solved, I do:

sudo apt-get build-dep inkscape;

but I get the following output:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Build-dependencies for inkscape could not be satisfied.

Apparently, I got some dependency problem, but there is no further 
information. With which command can I find out which build-dependencies can't be satisfied and why?

cheers,
Bram

---

### Post by Seisen on 2007-05-02
Post your source list.

---

