---
title: "GCJ/GIJ problems"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Xilon on 2006-05-08
I'm trying to compile a program with a custom "B102.jar" package. The package is basically used for keyboard input provided by my Uni. In order to include it I tried using```
javac -classpath ${CLASSPATH}:B102.jar prac8.java
```
but upon running```
$ java prac8
Exception in thread "main" java.lang.NoClassDefFoundError: prac8
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: B102.TextInputStream not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more

```It's like the default classpath gets omitted. Any ideas on how to include the jar file?

---

### Post by Xilon on 2006-05-09
Bump.

I no one can answer this then what Java IDEs would you suggest?

---

### Post by JKoder on 2006-05-09
I suggest using Eclipse, this is what i use and work well !
Good Luck !

---

