---
title: "where is java installed"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by docetes on 2007-02-19
can anyone tell where java is installed? I used apt-get to install it.

Thanks,
Dave

---

### Post by Maestro23 on 2007-02-19
> **docetes said:**
> can anyone tell where java is installed? I used apt-get to install it.

Thanks,
Dave

The .bin is [COLOR="Red"] /usr/bin/java[/COLOR]

Terminal command: which java
or locate java, or whereis java

---

### Post by docetes on 2007-02-19
sorry i made a mistake 
where is  the Java 2 SDK

thanks
DAve

---

### Post by docetes on 2007-02-19
bump

---

### Post by phossal on 2007-02-20
Here is the command to find the path of the java called from the command line.
```
ls -l $(type -path -all java)
```
The output will likely point to  */etc/alternatives/java*. 
So find out where *that* points by issuing ls -l like this:
```
ls -l /etc/alternatives/java
```
You can keep doing that until you get to the root.

---

