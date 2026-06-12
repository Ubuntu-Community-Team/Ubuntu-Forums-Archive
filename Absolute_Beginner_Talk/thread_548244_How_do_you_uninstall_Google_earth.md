---
title: "How do you uninstall Google earth?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by jwandc3 on 2007-09-11
I installed Google earth with Automatix but it reboots Ubuntu every time I try to start it up; not an uncommon occurrence according to other posts. Never mind, I can run it on Windows.

Strangely, though I can't uninstall it as Automatix doesn't list it as one of the installed programs; somehow it forgot! :)

Can anyone tell me a simple way to get rid of it?

---

### Post by useResa on 2007-09-11
I am not sure if Automatix does install it the same way as when downloading it yourself (which I have done), but I have a google-earth directory in my home directory.
```
cd ~/google-earth
```In this directory there is an uninstall script
```
 sh ./uninstall
```This should remove the installation.

BTW: Google earth is available now from the (medibuntu) repositories
```
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 11, 09:38 $ sudo aptitude search googleearth
p   googleearth                                        - Google Earth! - Explore, Search and Discover - binary files  
p   googleearth-data                                   - Google Earth! - Explore, Search and Discover - data files
```

---

