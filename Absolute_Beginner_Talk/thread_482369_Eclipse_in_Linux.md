---
title: "Eclipse in Linux?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by NS2-10 on 2007-06-23
Hey!

I'm a bit of a noob, but would someone please write a comprehensive guide of everything that needs to be done to get Eclipse to run applets on Linux (Feisty Fawn).

Using "apt-get install" commands I have tried to get it working, but I still get the same error message:

```
Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/dlang/workspace/AppletTester/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
```

Why?? Is something not properly installed?

Cheers!

---

### Post by pnix on 2007-06-23
You need to install sun java.
```
sudo aptitude install sun-java6-jdk
```

---

### Post by NS2-10 on 2007-06-24
I did this already and the error is still present. I have tried to install all sorts of JAVA packets but none of them removes the error...

Please come with more suggestions of how to solve this!!

---

### Post by BobCFC on 2007-06-24
I haven't done Java for over 5 years but it was always down to the CLASSPATH for me.

---

### Post by nick_h on 2007-06-24
Look in Preferences > Java > Inatalled JREs
Is is pointing to the right place?

---

### Post by kpkeerthi on 2007-06-24
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by NS2-10 on 2007-06-24
Haha, well thanks folks, but you must realize I am a noob...

First of all, what is CLASSPATH?

Where should JRE point?

Please help a lost soul :)

---

### Post by masklinov on 2007-07-01
Go to Window->Preferences, find the node Java->Installed JRE's. You probably can only see one option there, something like "java-1.4.2-gcj-4.1.-1.4.2.0" and it's location. You need to add a 1.5 or 1.6 JRE. To do this click Add and browse to the jre home directory, you should find it in /usr/lib/jvm/(java 1.5 or 1.6 folder). Click ok and select it.

---

