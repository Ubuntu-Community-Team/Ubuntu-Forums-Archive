---
title: "Path to JDK directory"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-09-24
I am trying to install bluej and it is asking what the path is to my JAVA (JDK) directory is. I have looked on the forum and not really found an answer. Can anyone tell me where java 6 should have have put this directory?

---

### Post by Hospadar on 2007-09-24
well you can do a couple things.

you may be able to do ```
echo $JAVA_HOME
``` or ```
env |grep JAVA
```or you can go into synaptic, find the jdk environment in question, right click it and go to properties and have a look at the "installed files" tab, or try a ```
which java
```Just off top of my head i think it's in /usr/bin/jvm or /usr/lib/jvm or /usr/bin/java or something like that

---

### Post by mevets on 2007-09-24
Was in
[QUOTE]/usr/lib/jvm/java-6-sun-1.6.0.00//QUOTE]
and I didnt not have the JDK installed

---

