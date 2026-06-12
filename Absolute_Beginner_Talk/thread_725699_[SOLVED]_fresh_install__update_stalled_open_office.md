---
title: "[SOLVED] fresh install  update stalled open office core"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-03-15
just installed fresh copy of ubuntu 7.10  then installing updates  but update stalled at open office.org-core 
all updates downloaded they stared installing but like I said stalled at the open office
so now what. 
 I still have the update manager open

---

### Post by PmDematagoda on 2008-03-15
Do:-
```
sudo apt-get install -f
```
and then:-
```
sudo dpkg --configure -a
```
Post the results of the two commands.

---

### Post by Doorslammer on 2008-03-15
well  it won´t let me close the update manager

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by PmDematagoda on 2008-03-16
Are you running any other package manager processes?

If not, then execute:-
```
sudo rm /var/lib/dpkg/lock
```
and then run the two commands mentioned before.

---

### Post by Doorslammer on 2008-03-16
yes  the** update manager** is still runing ! 

but it&#347; stalled it&#347; been about an hour stalled  at the open office.org-core  ( trying to install the update . everything downloaded fine but stalled  when installing .

---

### Post by PmDematagoda on 2008-03-16
Close the update manager and then try installing the updates manually through the commands I gave previously.

---

