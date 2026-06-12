---
title: "export comand not working"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-12-11
:~$ export HOME= /home/nolan/Desktop/Documents
bash: export: `/home/nolan/Desktop/Documents': not a valid identifier
Any Ideas?

---

### Post by subs on 2007-12-11
i think u have messed up your .bashrc and .bash and .bash_profile

try this...

> mv  .bash_profile oldbash_profile 
mv  .bashrc  oldbashrc 
then log out and log in


btw.... just post the results for...
> 
cat oldbashrc
cat oldbash_profile

tehn we can figure out what went wrong...

---

### Post by swoll1980 on 2007-12-11
do you want those posted before I run those comands or after?

---

### Post by swoll1980 on 2007-12-11
output is "no such file or directory"

---

