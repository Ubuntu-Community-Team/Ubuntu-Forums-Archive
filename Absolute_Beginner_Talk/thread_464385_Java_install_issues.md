---
title: "Java install issues"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by -Soul_Reaper- on 2007-06-04
> hugo@IJA-desktop:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
hugo@IJA-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
hugo@IJA-desktop:~$ 

There is the stuff i did in the console. I typed: > sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts then it gives the the error message wanting me to manually type: 'dpkg --configure -a' . But it gives me a error saying > dpkg: requested operation requires superuser privilege

Any help is appreciated! Also i got the java from the ubuntu wiki.

---

### Post by oilchangeguy on 2007-06-04
in terminal type, sudo dpkg --configure -a

---

### Post by Kobalt on 2007-06-04
Try ```
sudo dpkg --configure -a
```

---

### Post by -Soul_Reaper- on 2007-06-04
> **oilchangeguy said:**
> in terminal type, sudo dpkg --configure -a

Thanks that worked.:D

---

### Post by -Soul_Reaper- on 2007-06-04
Wait, how do i accept the agreement?

---

### Post by taurus on 2007-06-04
> **-Soul_Reaper- said:**
> Wait, how do i accept the agreement?

Use the Tab key to highlight the <OK> and then Return.

---

### Post by -Soul_Reaper- on 2007-06-04
Thanks :D

---

