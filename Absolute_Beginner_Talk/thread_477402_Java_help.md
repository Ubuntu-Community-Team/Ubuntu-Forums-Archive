---
title: "Java help"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-06-18
I want to run this one .jar file, and I'm using the command: 

```
java -jar GeminusClient.jar
```

However I'm receiving this as the output:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bot (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
```

Can anyone tell me what I should do to fix this? It seems to be something about versions.

---

### Post by Baelfael on 2007-06-18
Alright nevermind I fixed that.

I have another question though.

To open this file, I have to type 'cd Desktop', and then 'cd RSClassic', and then 'java -jar GeminusClient.jar'. Is there a way to make that a launcher on my desktop?

---

### Post by zanglang on 2007-06-18
You can create an empty text file and paste this in:
```
#!/bin/bash
cd ~/Desktop
java -jar GeminusClient.jar
```
Save it then you should be able to launch it by double-clicking.

---

