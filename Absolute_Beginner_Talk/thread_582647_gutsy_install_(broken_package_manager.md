---
title: "gutsy install (broken package manager"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-20
I think my package manager is broken output is below

rdsii64@rdsii64:~$ sudo apt-get update
[sudo] password for rdsii64:
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
rdsii64@rdsii64:~$ 
rdsii64@rdsii64:~$ sudo apt-get install -f
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
rdsii64@rdsii64:~$

---

### Post by Arthur Archnix on 2007-10-20
That's odd. What is in this file?
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by rdsii64 on 2007-10-20
> **Arthur Archnix said:**
> That's odd. What is in this file?
```
gksudo gedit /etc/apt/sources.list
```

thanks for the help but I nuked the install and reinstalled gutsy again.
when I get it up I will ask for some help setting up my sources list.

thanks for the reply though

---

### Post by rdsii64 on 2007-10-20
> **rdsii64 said:**
> thanks for the help but I nuked the install and reinstalled gutsy again.
when I get it up I will ask for some help setting up my sources list.

thanks for the reply though

got gutsy reinstalled, got automatrix working and my sources seem fine now.
thanks for the help anyway

---

