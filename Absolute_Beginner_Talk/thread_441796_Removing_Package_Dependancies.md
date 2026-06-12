---
title: "Removing Package Dependancies"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-05-12
When I uninstall a program that required me to download dependancies, are they removed along with the program? How can I remove the packages? Also, how can I tell what packages other packages depend on?

---

### Post by FuturePast on 2007-05-12
```
$ sudo apt-get autoremove
```
To see package dependencies you can right-click->Properties in Synaptic or
```
$ dpkg -s <package-name>
```

---

### Post by bobplano on 2007-05-12
well i know for sure that if you used aptitude to install it, the dependencies will be removed along with it.

---

