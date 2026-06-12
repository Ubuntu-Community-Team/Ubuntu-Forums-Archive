---
title: "dependency is not satisified"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-06-01
Doyou know how to go around it?
While trying to install new software, it said:," Error: Dependency is not satisifable: atlas3-base|lapack3|liblapack.so.3

---

### Post by %hMa@?b&lt;C on 2006-06-01
what are you trying to install?
does this command help at all?
```
sudo apt-get -f install
```

---

### Post by az on 2006-06-01
[QUOTE=ph7klw]Doyou know how to go around it?
While trying to install new software, it said:," Error: Dependency is not satisifable: atlas3-base|lapack3|liblapack.so.3[/QUOTE]
Do you have any non-ubuntu repositories enabled and did you try to install a non-ubuntu package?

---

### Post by blackjack6.21.91 on 2006-06-02
if you are trying to get dependencies not available in synaptic, then you can usually google them and download some kindof debian from the homepage

---

### Post by ph7klw on 2006-06-03
what is dependency? Does it mean that I need atlas3-base, lapack and liblapack.so.3 to install?

---

### Post by chameleon_789 on 2006-06-03
Usually it means the program needs those librarys/programs to function, although in some cases you will already have them installed under different names. 

You can force an install with **sudo apt-get install --force-depends **packagename****, but in synaptic it will list the package as broken and force you to uninstall it before you can install anything else. If it the package you forced doesn't work it's no biggie, but if it does work it's quite annoying not being able to install anything else (there's a way round that [here]("http://www.ubuntuforums.org/showthread.php?t=187293") though).

---

### Post by chameleon_789 on 2006-06-03
Actually looking at my synaptic I have atlas3-base and lapack3.. go to settings / repositories in synaptic and edit Ubuntu 6.06 (binary), then add universe and multiverse repositories and click reload. That will probably satisfy the dependencys for you automatically.

---

