---
title: "jdk Java5"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by cvockrodt on 2007-01-23
hey im trying to install an spp in java, and it's asking for the jdk directory.

i dont know where that is.

ive tried sudo update-alternatives --config java

and it returns this:
 Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

but i dont believe that is what i am looking for...

java returns an error message when i try to load any random file into the jdk directory
and it reads: 
The java file you have selected is not a valid jdk directory. The jdk directory is the directory that jdk was installed to. It must have a subdirectory "lib" with a file named tools.jar


i need help finding it in my file system.

---

### Post by sardion on 2007-01-23
You may have only installed the JRE (Java Runtime Environment) and not the whole JDK.  Install the package "sun-java5-jdk" which is in the multiverse repos.  Then you should have the whole JDK and all should work fine.

---

