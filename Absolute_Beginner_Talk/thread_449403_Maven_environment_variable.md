---
title: "Maven environment variable"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by cytutchi on 2007-05-20
Hi guys...

just installed maven for those who know n it asks me to do something that i don't know how to do and i think that is going to be useful since prob. many other installations will ask the same as well.

1. How to define e.g. Maven_Home environment variable (i understand that is the directory i just unpacked the Maven but m not understanding+don't know what to do)

2.add MAVEN_HOME/bin to your path so that you can run the scripts provided with Maven. (how can i add this to the path?)

Thenx in advance !!!

---

### Post by ounn on 2007-05-20
In the terminal execute the  following command for each terminal instance that you open

```
export MAVEN_HOME= {MAVEN INSTALL DIR} 
export PATH=$MAVEN_HOME/bin;PATH
```


without the {}


If you wish to have that variable always available without run this command you need to add this to some file somewhere at /var (sorry i don't know exactly where right now)


ounn

---

### Post by cytutchi on 2007-05-20
thenx mate!!!
appreciate it!

;)

---

