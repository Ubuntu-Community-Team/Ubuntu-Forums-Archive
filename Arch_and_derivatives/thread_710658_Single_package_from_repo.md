---
title: "Single package from repo"
date: 2008-02-28
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-02-28
Is it possible to have a single package from the testing repo? I'd like to get a few packages from testing, but not let it go over everything. I'm gussing I could enable the repo, grab the packages, and then disable it but then running pacman -Syu wouldn't get those packages and if I readded the repo and did that, it would give me some I didn't want.

---

### Post by mips on 2008-02-28
Yes you can do that. As far as I know the testing packages are uniquely named as testing so they can not be confused with the stable ones etc.

---

### Post by fwojciec on 2008-02-28
First of all -- make sure that testing repo is listed in pacman.conf as the last repo (the order of repos determines the repos from which packages will be taken by default).  Then you can override the default preference and install from the testing repo by doing "pacman -Sy testing/package".

---

### Post by Crooksey on 2008-02-29
Why not just point your browser to the location of the repo, then manually grab the package and install that way?

---

