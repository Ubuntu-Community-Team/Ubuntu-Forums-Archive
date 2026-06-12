---
title: "amule adunanza"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2007-10-11
hallo i have installed the new patched version of amule adunanza.

i have used 3 comand......./configure.....make install.......make

now i want unistall this software. can you help me?

---

### Post by cacharreo on 2007-10-11
Edit your sources.list file:
[I]**sudo gedit /etc/apt/sources.list** 
[/I]
include the next line on your repositories:
[I]**deb [http://amule-adunanza.marleylandia.com/ubuntu/ramko-sonne/3.11b/edgy](http://amule-adunanza.marleylandia.com/ubuntu/ramko-sonne/3.11b/edgy) i386/ **
[/I]
Now:
***sudo apt-get update***
And then:
 ***sudo apt-get install amule-adunanza***
That's all!!

---

### Post by cacharreo on 2007-10-11
Sorry I mistake your question.This answer is to INSATALL it

---

