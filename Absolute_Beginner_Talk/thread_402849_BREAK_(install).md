---
title: "BREAK (install)"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by 5ER on 2007-04-06
A lot of packages don't want to be installed. In adept it says "BREAK (install)" as requested operation. Apt-get in console says that it simply can't be installed. WTF

---

### Post by zvacet on 2007-04-06
I´m not familyar with Adept but it seems it gives you massages that youhsve broken packages.Until you solve that problem no other packages can not be installed.Try to find in Adept (maybe under edit) command wich fixes broken packages.

---

### Post by 5ER on 2007-04-06
some (most, I think...hope) packages do install.

Can you give me the command for apt-get to fix packages?

---

### Post by taurus on 2007-04-06
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Aircooledmadness on 2007-04-06
try a 

sudo dpkg --configure -a

That will try to fix any problems with half-installed or broken packages.

---

### Post by 5ER on 2007-04-06
> **taurus said:**
> What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```
I have all the latest packages, everything upgraded.

> **Aircooledmadness said:**
> try a 

sudo dpkg --configure -a

That will try to fix any problems with half-installed or broken packages.
Doesn't work :(

---

### Post by zvacet on 2007-04-06
If you can download and install new programs then your problem is solved.

---

### Post by 5ER on 2007-04-07
Some packages I can install, some I can't.

---

### Post by zvacet on 2007-04-07
Do you have all repositories open?
[https://help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu")

Or if you are runing Edgy system>administration>software properties(this is in Gnome but I belive something similar exist in KDE)

---

