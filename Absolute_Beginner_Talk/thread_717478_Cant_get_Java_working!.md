---
title: "Cant get Java working!"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by OliH on 2008-03-07
Hi,

I have been trying to install Java and JRE on Ubuntu 8.04 (Wubi installation) and have been having difficulty - Firefox never seems to recognise it even though I've downloaded the plugins numerous times, OpenOffice doesn't recognise the JRE when I try to write scripts, and there are other problems with other programs too. 

Basically I think I've installed Java and JRE incorrectly - can anyone help?

When I type:
```

sudo update-alternatives --config java
```
I get:
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
```
When I type the command "java - version" I get:
```
java version "1.4.2_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_05-b04)
Java HotSpot(TM) Client VM (build 1.4.2_05-b04, mixed mode)
```
Many thanks in advance,

Oli

---

### Post by kesman on 2008-03-07
Seems like a bug in Hardy. Remember that it's in alfa stage, and not very stable. Use Edgy (7.10) instead.

---

