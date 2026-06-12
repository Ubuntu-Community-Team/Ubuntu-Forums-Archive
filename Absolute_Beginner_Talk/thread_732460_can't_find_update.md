---
title: "can't find update"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by scottc992004 on 2008-03-22
I can't run sudo apt-get install update from terminal.

mdk@mdk:~$ sudo apt-get install update
[sudo] password for mdk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
mdk@mdk:~$

---

### Post by munkyeetr on 2008-03-22
Are you sure you want to run **install** update? And not just update, to update your package list?
```

sudo apt-get update

```

---

### Post by Oldsoldier2003 on 2008-03-22
> **scottc992004 said:**
> I can't run sudo apt-get install update from terminal.

mdk@mdk:~$ sudo apt-get install update
[sudo] password for mdk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
mdk@mdk:~$
to update your package lists:
```
sudo apt-get update
```

then 
```
sudo apt-get upgrade
```
to upgrade your installed packages

---

### Post by scottc992004 on 2008-03-22
thanks i forgot no install

---

