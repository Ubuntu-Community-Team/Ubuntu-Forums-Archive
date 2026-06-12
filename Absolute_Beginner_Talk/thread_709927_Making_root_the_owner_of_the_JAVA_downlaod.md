---
title: "Making root the owner of the JAVA downlaod"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Vithant on 2008-02-27
I downloaded the Java Se development program from sun. I should have put in tmp instead of public according to the message I got. Root has to own the Java download, how do I accomplish that. Do I cd to tmp?

Thanks

---

### Post by igknighted on 2008-02-27
You want the Java SDK installed?  This is in the repo's, use 'sudo apt-get install sun-java6-jdk' to install it.  Netbeans should be available as well if you want the IDE too.

EDIT: There are many complications trying to use the package from sun.  It is possible, but you would need a very good reason to use that instead of the repo version.

---

### Post by asmoore82 on 2008-02-27
> **igknighted said:**
> You want the Java SDK installed?  This is in the repo's, use 'sudo apt-get install sun-java6-jdk' to install it.  Netbeans should be available as well if you want the IDE too.

EDIT: There are many complications trying to use the package from sun.  It is possible, but you would need a very good reason to use that instead of the repo version.

+1, Well put

you could also Open "System -> Administration -> Synaptic Package Manager" and search for "java"

---

### Post by Vithant on 2008-02-28
how do I stop it from trying to install the sun product?

Thanks 
Jim

---

### Post by igknighted on 2008-02-28
The package in the repo's is the sun package ( i think they have java5, java6 and the open source version called icedtea, also called java7.  Java 5 and 6 are almost the same, I would recommend java6 because it is newer (security fixes and more compatible with new things that come out).  To install, simply install the package sun-java6-jdk (use either synaptic or apt-get from the CLI... if in Kubuntu do NOT use Adept).  I think it will bring in the plugin, but if you still can't load java applets in your browser (and are not using 64bit), then you may need to also install sun-java6-plugin

---

