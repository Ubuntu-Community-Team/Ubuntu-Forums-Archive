---
title: "check versions of packages?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by jms830 on 2006-05-03
how can i check the versions of packages i have installed
and how can i check the versions of a package in the repositories? 
I'm comfortable with the terminal. Thanks

---

### Post by nanotube on 2006-05-03
heh well, the easiest way is to open up the synaptic package manager, search for your package, and it will list the version you have installed, and the versions that are available in the various repositories, for that package.

the commandline version to get the version you have installed is 
```
dpkg -l packagename
```
but i dont know the exact commandline way to check the version in the repositories... probably something with apt-get or one of its friends ;)

---

