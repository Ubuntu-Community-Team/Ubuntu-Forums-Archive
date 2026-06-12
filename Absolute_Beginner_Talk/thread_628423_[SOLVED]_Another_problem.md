---
title: "[SOLVED] Another problem"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-12-01
ok i have another problem with my mates laptop now when you try to install stuff from repo's 
u get this error....
```
Kopete cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

---

### Post by PmDematagoda on 2007-12-01
kamitsukai it seems you have the same cause which is causing your first problem, if we can solve it, then even your second problem is also solved.

---

### Post by seventhc on 2007-12-01
I would try itby going to applications>Add/Remove then make sure the top right corner is set to 'all open sorce applications' or 'all available applications' ( both will work) then click on internet and then type kopete into the search box, you can probably just type kop if you want. either way, kopete will show up put a check mark in the box, click apply,it will ask you for the root password. once you enter it it should install. :)

---

### Post by seventhc on 2007-12-01
> **PmDematagoda said:**
> kamitsukai it seems you have the same cause which is causing your first problem, if we can solve it, then even your second problem is also solved.

what was the first problem???:S

---

### Post by PmDematagoda on 2007-12-01
The first problem is [this]("http://ubuntuforums.org/showthread.php?t=628418"), if you look carefully you can see they are linked.

Anyway, assuming that it is the problem which I think it is, do this:-

Open up Software Sources in System>Administration>Software Sources, when it opens up, enable all the choices in the Ubuntu Software tab except for the CD and also enable everything in the Updates tab except for "Pre-released updates". After they are done, close the window, you will be asked to reload the software sources, do it, once that is done, try doing:-
```

sudo apt-get install -f
```

Again and then try installing the software you need.

---

### Post by seventhc on 2007-12-01
> **PmDematagoda said:**
> The first problem is [this]("http://ubuntuforums.org/showthread.php?t=628418"), if you look carefully you can see they are linked.

Anyway, assuming that it is the problem which I think it is, do this:-

Open up Software Sources in System>Administration>Software Sources, when it opens up, enable all the choices in the Ubuntu Software tab except for the CD and also enable everything in the Updates tab except for "Pre-released updates". After they are done, close the window, you will be asked to reload the software sources, do it, once that is done, try doing:-
```

sudo apt-get install -f
```Again and then try installing the software you need.

ah, ok I see but I thought all those choices were enabled by default in Gutsy,I'm not positive but I remember checking them on mine but don't remember having to change anything.
Then again I'm not to sure if he's using Gutsy or not, anyway I hope it works for him. :)

---

