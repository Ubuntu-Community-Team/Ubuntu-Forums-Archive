---
title: "Serious problems with Java and JDK +Netbeans IDE"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by chr on 2007-08-27
Hello you all,

yesterday my ubuntu os chrashed and i forced the system to shut down.

after that my JDK together with netbeans didn't work anymore. i tried to uninstall and then reinstall the programm again, but it doesn't work.

now i cant compile aor run java programs, and even a fresh installed JDK+netbeans wont't open correctly. 

is there someone who has an advice, I don't want to reinstall my hole ubuntu OS.

best regards

christoph

---

### Post by bjarneh on 2007-08-27
what happens when you try to compile a Java program ie.

outprint of:

javac SomeClass.java

---

### Post by chr on 2007-08-27
now i could compile it but don't run it...

and if i want to run it in e.g. eclipse this is the output:

Exception in thread "main" java.lang.NoClassDefFoundError: Formel
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: Formel not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/christoph/workspace/Christoph/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

---

### Post by chr on 2007-08-27
no one any ideas?

chr

---

### Post by chr on 2007-08-28
hello,

still searching for an answer. i'm in trouble trouble, because i need a java development environment for my studies at the uni.

brgds

chr

---

### Post by Elegorod on 2007-08-30
If you have
Exception in thread "main" java.lang.NoClassDefFoundError: Formel
at **gnu.java.lang.MainThread.run**
then 
```
sudo update-alternatives --config java
```
And choose Sun java you have installed

Now, run netbeans in terminal, What's the output?

---

