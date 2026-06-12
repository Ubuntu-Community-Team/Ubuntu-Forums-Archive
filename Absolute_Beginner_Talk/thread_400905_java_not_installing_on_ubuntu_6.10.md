---
title: "java not installing on ubuntu 6.10"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by deepaksin1 on 2007-04-04
hi,
i have installed ubuntu 6.10 recently on my machine .I have an AMD X2 2200+ ,but whenever i try to install java it does not do it. in the add remove programmes option from where we install the essential programmes all the jdk's there say that this installation is not supported on your computer ,

please advice ,
thanx

---

### Post by DSn0wMan on 2007-04-04
Does it work from the terminal

```
sudo apt-get install sun-java5-jdk 
```

If it does not work please post the error message.

---

### Post by zvacet on 2007-04-04
Open all your repositories.After that
```
sudo aptitude update && sudo aptitude upgrade
```
Go to the synaptic and in the search box type **sun**

---

### Post by mikewhatever on 2007-04-04
Yes, you have to enable Universe and Multiverse repositories in System>Administration>Software Sourses

---

### Post by deepaksin1 on 2007-04-04
hi guys ,
thanks for all your help , i just went to the terminal and used the command provided above and it did the work .i hope that the java environment works fine on my computer now.

thanks again

---

