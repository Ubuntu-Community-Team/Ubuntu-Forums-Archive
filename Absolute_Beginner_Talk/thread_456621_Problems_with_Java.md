---
title: "Problems with Java"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by SaitoSan on 2007-05-27
when i tried to run a java class i get the following message
> 
Exception in thread "main" java.lang.ClassFormatError: WhateverClass (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)


But if i run it in windows, it's perfectly okay.

Running ```
java -version
``` gives me this 
> java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


But I've installed java6 jre; why it says that my jre version is 1.4.2???. My java compiler version is javac 1.6.0. I think the problem is caused by the difference in version between jre and javac; version 1.4.2 vs version 1.6.0. How do I change the jre to version 1.6?

Thx for the help.

---

### Post by deadgobby on 2007-05-27
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=java&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=java&titlesearch=Titles)

---

