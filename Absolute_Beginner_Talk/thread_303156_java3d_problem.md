---
title: "java3d problem"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-19
I have the following error for all java3d programs:

Exception in thread "main" java.lang.UnsatisfiedLinkError: no j3dcore-ogl in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at javax.media.j3d.MasterControl$6.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.media.j3d.MasterControl.loadLibraries(Unknown Source)
        at javax.media.j3d.VirtualUniverse.<clinit>(Unknown Source)
        at Ball.<init>(Ball.java:15)
        at Ball.main(Ball.java:55)
Java Result: 1

Substitute Ball with the name of the class, its does the same for all java3d Apps.

Anyone know what the prob is?

Thanks, Tom

---

### Post by ViGiLnT on 2007-05-02
If anyone comes across this problem as I did, you have to do this:

Copy the files "libj3dcore-ogl-cg.so"  and "libj3dcore-ogl.so" into the "/jre/lib/i386/"  directory of the Java version you are using. In my case it was:

/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/

---

### Post by henrybrad on 2007-12-29
Thank you, that fixed my problem instantly.

---

