---
title: "Anybody encounters this ? Ubuntu 7.04"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by spalicha on 2007-05-29
Anybody encounters this ? Ubuntu 7.04 
I have upgraded from 6.06-> 6.10 - 7.06

sudo apt-get install camorama
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package camorama

---

### Post by deadgobby on 2007-05-29
Yes and no.Yet, I did install it just fine in Synaptic.
 Some time using aptitude instead of apt-get can work too.
Gobby

---

### Post by jasonlfunk on 2007-05-29
Make sure you have the universe repository enabled. System -> Administration -> Software Sources

---

### Post by spalicha on 2007-05-31
Thanks Jason. That was it. universe repository was not enabled.

---

