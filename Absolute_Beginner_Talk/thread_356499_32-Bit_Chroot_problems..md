---
title: "32-Bit Chroot problems."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by RaiFox on 2007-02-08
Hi, I've been trying to install a 32-Bit chroot.

Ive been using this guide [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

First thing it says to do is type "sudo apt-get install dchroot debootstrap" in a command prompt (or w/e its called), it than gives me an error: "Couldn't find package dchroot".


I'm using 6.06 LTS

---

### Post by schorsch on 2007-02-08
Hi,

it is in the "universe"repository. Do you have this repository enabled for install?

---

### Post by benuski on 2007-02-08
Do you have the Universe repository enabled?  Because I checked, and that is the repository in which that package is found.  If not, [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") link should help you out.

---

