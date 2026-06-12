---
title: "Get list of available packages using apt-get"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by pranith on 2006-11-22
How do i get the list of available packages and their info using apt-get :confused: ?? Like yum does it using "yum list available" and "yum info available" ....shows the architecture, version etc..How can i do that using apt-get or apt-utils maybe ??:-k

---

### Post by unarmedninja on 2006-11-22
after you do "apt-get update" to refresh your sources.list file you can type "dselect" in the console (this works in most debian distros but i havent tried in ubuntu). 
you can also do "apt-cache search (search term)" to find a specific package.
If i were you i would just use synaptic, its much easier for beginners to use. (system->administration->synaptic package manager)

good luck.

---

### Post by CatKiller on 2006-11-22
If you don't want to use Synaptic - because you're on the command line, maybe - then

```
sudo aptitude
```

can get you a list of all the stuff in the repositories.

Otherwise, ```
sudo aptitude search <*keyword*>
sudo aptitude show <*packagename*>
``` will give you information on a particular package.

---

