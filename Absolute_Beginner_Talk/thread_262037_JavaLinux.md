---
title: "Java/Linux"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Ixhabbaba on 2006-09-21
Hi! I'm kind of new to Ubuntu, but have been writing Java for a while in Windows, so naturally I want to continue doing so in Ubunt. I have downloaded and installed Java EE 5, but have two small problems:

1. I don't know how to set the classpath. A book I have tells me to use the command 
setenv CLASSPATH (paths separated by colons)
which bash says doesn't exist. Can someone tell me how to do this, permanently if possible?

2. I tried to run some of my old java creations, which worked fine as long as they were text based. When I try to run a graphical class, java says that it cannot load awt. The output looks like this:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at Direkt4.<init>(Direkt4.java:3)
   at Direkt4.main(Direkt4.java:8)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...6 more

I've never seen this type of error before, and I'm therefore very confused. Could someone tell me how to fix this?

                                         Ixhabbaba

---

### Post by amo-ej1 on 2006-09-21
About the classpath:

```

edb@lap:~$ export CLASSPATH="/my/class/path"
edb@lap:~$ echo $CLASSPATH
/my/class/path

```

But be aware this variable is only set in your current shell. If you want to make it permanent for all instances of bash you should add it to the file .bashrc in your home directory (which gets executed every time you launch a new shell.


About your previous creations:

when you run java -version you will see something like:
edb@lapedb:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Which means now you are using the 'gnu' java implementation (which lacks some functionality). 

So you should install java the ubuntu way and use update-alternatives to choose which jre/jdk you wish to use


```

edb@lapedb:~$ update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/jvm/java-gcj/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1041
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/jre/bin/java.
root@lapedb:/home/edb# update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
root@lapedb:/home/edb# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

tada ;)

---

