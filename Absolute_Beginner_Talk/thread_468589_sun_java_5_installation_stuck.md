---
title: "sun java 5 installation stuck"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by edison118 on 2007-06-09
i tried to install Java 5.0 Runtime in Ubuntu 7.04

during the installation it showed a license agreement. but i can't see a  tab for accept the agreement. so i closed the window. 

now when i  open synaptic package Manage it gives me the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

pls tell me how to solve this problem

---

### Post by zvacet on 2007-06-09
```
sudo dpkg --configure -a
```

When you come to the licence agreement you will see little box on the left.Chek it and hit forward.

---

### Post by edison118 on 2007-06-09
when i typed the command it showed the following

sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

edison@edison-desktop:~$ 

when I run the synaptic package Manager it shows

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

when i checked the broken filter it shows sun-java5-bin

should i remove/uninstall the java or can it be repaired.

---

### Post by zvacet on 2007-06-09
**synaptic>edit>fix broken package**

---

