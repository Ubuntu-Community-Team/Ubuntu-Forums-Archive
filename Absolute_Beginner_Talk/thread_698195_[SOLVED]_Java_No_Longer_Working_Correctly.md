---
title: "[SOLVED] Java No Longer Working Correctly"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by deathblossom on 2008-02-16
Hey guys, I think I screwed up Java JDK on my computer. It was working perfectly before, but I started taking a Java class and the officially supported version is Java 5. So, I removed Java 6 and reinstalled Java 5, and now it's borked. So, I reinstalled Java 6 and changed the working Java version to once again be six, and it's still borked. I can't exactly tell you what's *wrong* with it. What I know is that programs I wrote that worked before, no longer work. For example, I'm getting this multiple errors about things not being able to resolve to a type and this; 

The method printf(String, Object[]) in the type PrintStream is not applicable for the arguments (String, double) [which I pick out because it's the only error I've managed to get besides "failure to resolve type" from much longer programs]

If someone could help me fix this (and perhaps also help me downgrade back to version 5), I'd appreciate it. Sorry I don't have anymore details.

Edit: 

So, I ran the already compiled versions of the files, and this is the error I get:

Exception in thread "main" java.lang.NoClassDefFoundError: 
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

More Edits:

So,  I can get some of the already compiled versions of files to run. But when I try to compile them now, they won't compile and I get all the resolve errors I mentioned before.

---

### Post by dustman on 2008-02-19
are you compiling these from the command line or from some IDE?

---

