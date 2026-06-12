---
title: "Automatix did not uninstall Java correctly"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-07-25
This is the problem I had.. the author outlines the solution....

[http://www.getautomatix.com/forum/index.php?showtopic=635](http://www.getautomatix.com/forum/index.php?showtopic=635)

BUT... i get this error when i type in the command.

update-alternatives: unable to open /var/lib/dpkg/alternatives/java.dpkg-new for write: Permission denied


Any help is appreciated. Thanks.

---

### Post by wolfen69 on 2007-07-25
try:
```
gksudo nautilus
```

this will allow full access to anything.

---

### Post by Seisen on 2007-07-25
try 

```
sudo rm /etc/alternatives/java
sudo update-alternatives --auto java
```

---

