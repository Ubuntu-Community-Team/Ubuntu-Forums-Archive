---
title: "Reinstalling ubuntu"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-24
Im on the verge of deleting ubuntu because i cant sort out two problems which are bugging me like hell !

1) cant play dvd because the New ATI driver I installed is to choppy and slow its like being back on vista:mad:
[http://ubuntuforums.org/showthread.php?t=588872](http://ubuntuforums.org/showthread.php?t=588872)

2)I cant log off then log back on again because of Kiba-dock
[http://ubuntuforums.org/showthread.php?t=588127](http://ubuntuforums.org/showthread.php?t=588127)

Please help with these im desperate!!!!!](*,)

---

### Post by realvz on 2007-10-24
about your 2nd problem 
try avant-window-navigator
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by kamitsukai on 2007-10-24
thanx but that covers how to install a new dock type program but i just want rid of kiba dock, maybe when im sorted i might try it

*Edit*
oops both links were the same

---

### Post by kamitsukai on 2007-10-24
<bump>

---

### Post by mali2297 on 2007-10-24
When you want to compile from source, use **checkinstal**l. You can get checkinstall from the repositories
```

sudo apt-get install checkinstall

```
or use Synaptic.

Now, if any instructions says **make install**, type **checkinstall** instead. Then you will be able to later uninstall the program through dpkg, apt-get or Synaptic.

It won't help you with your current problem but can be useful in the future.

---

### Post by Paqman on 2007-10-24
> **kamitsukai said:**
> thanx but that covers how to install a new dock type program but i just want rid of kiba dock, maybe when im sorted i might try it


Are you able to uninstall Kiba Dock with Synaptic? If so, then installing AWN instead will give you similar functionality. Apparently AWN is more stable than Kiba.

---

### Post by kamitsukai on 2007-10-24
thanx mali2297 i might try that next time

---

### Post by kamitsukai on 2007-10-24
? anyone

---

