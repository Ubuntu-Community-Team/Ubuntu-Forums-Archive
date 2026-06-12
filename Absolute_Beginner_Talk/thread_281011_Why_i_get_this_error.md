---
title: "Why i get this error ?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by stake on 2006-10-20
When i am trying to install something sometimes i get this error and i can't continue:

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is this and how can i fix it ? 

P.S: i am new in linux so i need help ... 

;)

---

### Post by Bachstelze on 2006-10-20
Hi and welcome to Ubuntu :)

You can only have one package management app (apt-get, aptitude, synaptic, adept, dpkg...) running at a time.

---

### Post by invalid on 2006-10-20
> **stake said:**
> When i am trying to install something sometimes i get this error and i can't continue:



What is this and how can i fix it ? 

P.S: i am new in linux so i need help ... 

;)

It sounds like you have more than one package manager operating at the same time. Try closing synaptic if you are using apt-get or another manager.

---

### Post by stake on 2006-10-20
thanku both ... i close the one but now i get this :

> E: Couldn't find package sun-java5-jre

it means that the package i want to install it was deleted ?

---

### Post by angkor on 2006-10-20
You probably need to enable some extra repositories to your /etc/apt/sources.list

Read this and post back if you have problems.

[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

---

