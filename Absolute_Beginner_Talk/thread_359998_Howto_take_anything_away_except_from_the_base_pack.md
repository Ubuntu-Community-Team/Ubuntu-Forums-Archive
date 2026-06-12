---
title: "Howto take anything away except from the base packages"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Neurobrainy on 2007-02-12
Hi!
After install xubuntu today i want to strip out anything installed except from the base system. I have on my Gentoo maschines a so called "world"-file with a minimum of additional packages that i need. Gentoo always tries to optimize the whole system to the package registered in the world file.

I like the wonderful usability in Ubuntu and i want to compete with my high, optimized Gentoo systems. If it is possible to build a comparable sytem in Ubuntu that might take 20 % more diskspace, memory, i might think about changing one or two maschines to Ubuntu just for the better usability.

I need a tool like aptitute, apt, synaptic or whatever that is able to protect the base system from deinstalling. Maybe a dependency tree might be enough, so i could just take away key-packages and the dependcies will follow.

P.S.: I use Debian 2 years ago, but i gave it up, after one package forced me to delete another one. The otherone was part of the package management. I was quite disappointed that it was possible to delete parts of the base system in debian. I dont want that again.

Thanks for any hint i get...

---

### Post by Neurobrainy on 2007-02-12
Okay, i solved it myself...sorry for replay to myself!!!!
Deinstall everything in aptitude, then select all you want and add the metapackage "minimal-ubuntu".....

---

