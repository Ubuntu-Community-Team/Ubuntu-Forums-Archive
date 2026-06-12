---
title: "What is different between dynamic glibc and static glibc?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-16
Hi
Thank you for reading my post
Can you explain what is different between following items and which one is suitable for Ubuntu 7.10?

 dynamic glibc-2.3
 dynamic glibc-2.3
 static glibc 2.2

Thanks.

---

### Post by ByteJuggler on 2008-01-16
Libraries are typically distributed with both a dynamic and static version.  So if you install, say the 2.2 package you'll get the static and dynamic glibc files installed.  Likewise with 2.3.  It looks like the "current" version in the repositories for Gutsy is [2.2]("http://http://packages.ubuntu.com/gutsy/libs/libstdc++2.10-glibc2.2").  

A static library is a library that gets statically linked into (copied into) your executable file when you link your final application during compilation.  It means the application doesn't have an external dependency on the library existing on any machine it might be run on, but increases the filesize of the executable.  

Conversely, dynamic libraries are like Windows .DLL's, they are shared and are provided to be linked to at application runtime.  So when you link to a dynamic library, the compiler will link stub code into your application that will cause the dynamic library to be loaded and linked in on the fly when you start the application.  Thus, you save the space used by linking a copy of the library (or the used parts of it) into your executable, but now your executable has this external dependency for the correct version of the shared library to be present on any system you want to run the program on.  If the library is missing, the application obviously wont run.  

LibC (GLibc) is one of the most commonly used libraries, almost every program will link to it, so there's a lot of benefit to having it as a shared library, as you can imagine.

---

### Post by ecoatmo on 2008-02-06
I am considering getting Ubuntu, but have a question:

What is the version of GLIBC that Ubuntu uses?  I need to have GLIBC_2.4 for a program that I intend to use.

According to a post 3 weeks ago, Gutsy uses GLIBC_2.2.  If this is true, is there a way to "upgrade" in Gutsy to a GLIBC_2.4, or is this not possible or a bad idea?

Thanks!

---

