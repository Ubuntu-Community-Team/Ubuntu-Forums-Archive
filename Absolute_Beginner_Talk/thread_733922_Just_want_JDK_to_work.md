---
title: "Just want JDK to work"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by TheaGanoe on 2008-03-24
in my /usr/bin folder, my javac link shows up as "link broken"

How do I fix it?  I want it to point to /usr/lib/jvm/java-6-sun

Gutsy, multiverse repository enabled

if I try this:

:~$ /usr/lib/jvm/java-6-sun/javac HelloWorld.java

result: Too many levels of symbolic links

---

### Post by neurostu on 2008-03-24
have you tried recreating the symbolic link with 
```

ln -s /usr/lib/jvm/java-6-sun/javac  /usr/bin/javac

```

I got this from:
[http://ubuntuforums.org/showthread.php?t=255573](http://ubuntuforums.org/showthread.php?t=255573)

---

### Post by TheaGanoe on 2008-03-24
nuerostu...thanks.  after I execute that command I still get

thea@thea-hp:~$ javac HelloWorld.java
The program 'javac' can be found in the following packages:
 * gcj-4.1
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * jikes-kaffe
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * ecj
 * sun-java5-jdk
 * jikes-sun
Try: sudo apt-get install <selected package>
bash: javac: command not found
thea@thea-hp:~$

---

### Post by TheaGanoe on 2008-03-24
Tried it again:

root@thea-hp:/home/thea# ln -s /usr/lib/jvm/java-6-sun/javac  /usr/bin/javac
ln: creating symbolic link `/usr/bin/javac' to `/usr/lib/jvm/java-6-sun/javac': File exists
root@thea-hp:/home/thea#

---

