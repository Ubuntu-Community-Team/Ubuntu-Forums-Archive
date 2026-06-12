---
title: "what command do i use to check if a package is installed?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by tee2 on 2006-11-28
nt


thank you.

---

### Post by syrleb on 2006-11-28
go to synaptic and search for the package, u will see if you have it or even in add or remove programs

---

### Post by nickburns on 2006-11-28
Don't know the command line but

System >> Synaptic 

Then Status Button on bottom left

Then choose the Installed option at top left

This is a list of all installed packages.

---

### Post by CatKiller on 2006-11-29
```
sudo aptitude search <*packagename*>
```

**i** means that it is installed
**p** means that it isn't
**c** means that it once was installed, but isn't now, and its config files remain
**v** means that it's only a pretend package anyway.

But Synaptic is prettier.

---

