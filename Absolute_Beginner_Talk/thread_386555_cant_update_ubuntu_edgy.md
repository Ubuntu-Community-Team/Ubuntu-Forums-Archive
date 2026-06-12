---
title: "cant update ubuntu edgy"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by super.rad on 2007-03-17
I've bought my computer into the lounge to plug it into the modem so i can try and sort out wireless. it's telling me i have 140 updates so i click install and it crashes my computer, i've tried doing it a few times but getting the same problem everytime. Also i read somewhere about enabling respotories (or something like that) is there a good beginners guide to running linux after installing it?

---

### Post by v8YKxgHe on 2007-03-17
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

There is a section in there about Software Repositories.

---

### Post by j.miller565 on 2007-03-17
you could always try downloading and installing your updates through the Terminal. 

Here are the codes:
```

sudo apt-get update
```

Then 

```

sudo apt-get upgrade
```

---

### Post by super.rad on 2007-03-17
that crashes the computer aswell, so does trying to add or remove programs. I'm a bit stuck so any ideas would be great. thanks

---

### Post by Kateikyoushi on 2007-03-17
Post the output of this.

```
free -m
```

---

### Post by super.rad on 2007-03-17
```
jimin@jimin-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           946        303        643          0         14        160
-/+ buffers/cache:        128        818
Swap:         1019          0       1019
jimin@jimin-desktop:~$ 
```

---

### Post by super.rad on 2007-03-17
i've now switched to kubuntu 6.10 as my wireless card works without any problems, but im still having the same problem with it crashing when i try to update. could this be because im trying to install 124 updates? any other ideas/solutions?

---

### Post by super.rad on 2007-03-19
ok well my wireless card worked fine in kubuntu dapper but not in edgy so i've switched back to ubuntu edgy as i prefer gnome. but im still having this problem, everytime i try to update, install anything it just freezes and i have to restart. any ideas guys? i really want to use ubuntu but if i cant work this out im going to have to stick with xp

---

### Post by zvacet on 2007-03-20
How did you upgrade?Via net?Try alternateCD.This is how to upgrade from it.
[https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrades%29%7C%28edgy%29]("https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrades%29%7C%28edgy%29")

---

### Post by super.rad on 2007-03-20
No i didnt have linux on my computer, did a fresh install of ununtu edgy, it crashes when i try to install any updates

---

