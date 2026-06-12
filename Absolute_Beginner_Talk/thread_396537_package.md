---
title: "package"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-29
hi there

i just installed a dsniff package with amptitude  install dsniff 

now i want to run dsniff , so how can i do that ?? and where i can find it

---

### Post by compmodder26 on 2007-03-29
In a terminal, type "dsniff" and see what happens.

---

### Post by ceezax on 2007-03-29
muhammad@muhammad-desktop:~$ dsniff
dsniff: nids_init: no suitable device found

---

### Post by compmodder26 on 2007-03-29
Well, the command is right.  But dsniff is having a problem.  Never used the program before, so I'm afraid I'm of little use at this point.

---

### Post by acidbom on 2007-04-08
you need to know what network card your using
example
eth0
ath0
ect....

then you use the -i flag to specify that card

like so.
 ross@ross-laptop:~$ dsniff -i ath0

hope that helps

---

### Post by encikraju on 2008-05-19
try sudo 
or better 
man dsniff

---

