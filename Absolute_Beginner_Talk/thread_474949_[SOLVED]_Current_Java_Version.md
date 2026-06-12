---
title: "[SOLVED] Current Java Version"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-06-15
I always get confused with which version of Java to install.  There is a site where I am having a problem joining the chat room and it requires the latest version of Java.  Here is what I have:

> java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

If this is not the current, what do I need to do?

---

### Post by wormser on 2007-06-15
It looks like I got the version updated.  But I am still having trouble entering this [chat room]("http://thomhartmann.com/chat.shtml").

> java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)



Can anybody enter this [chat room]("http://thomhartmann.com/chat.shtml")?

---

### Post by pnix on 2007-06-15
I think latest version is 1.6

---

### Post by pnix on 2007-06-15
try 
```
sudo apt-get install sun-java6-plugin
```

---

### Post by wormser on 2007-06-15
> **pnix said:**
> try 
```
sudo apt-get install sun-java6-plugin
```

That did the trick.  Thank you!

---

