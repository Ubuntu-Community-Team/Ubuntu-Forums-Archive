---
title: "Manual package installation caused corrupted packages in Synaptic"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Antesima on 2006-01-16
Hello,

being disappointed by the version of Kino / Tovid in the standard 
repositories of Synaptic (I'm with an Amd64), I managed to install the latest versions manually (by dpkg and compiling for tovid).

I was forced with dpkg to update some basic libraries such as cpp and gcc,
which are now marked corrupt by synaptic. Each time I want to update a package, Synaptic want to suppress all programs based on these corrupted libraries, so I can't use it anymore.

I downloaded the packages from [www.debian.org](www.debian.org), and I can't find
the correct repository from their site to add to synaptic (well their long
list is too long :) ).

Does anyone have an idea on how to fix this ?

Thanks in advance for your replies.

[Edit] My mistake : I meant "Broken packages" not corrupted.

My system : 
Amd 64 / Ubuntu 5.10 64 bit version

---

### Post by jasay on 2006-01-16
Sometimes with broken packages you can go to synaptic > custom (on the bottom left) > broken (left sidebar) and upgrade/fix the packages.  I don't have any broken packages to experiment with right now though.

---

