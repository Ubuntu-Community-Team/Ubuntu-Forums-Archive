---
title: "Install/Uninstall JMF"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by JayeD on 2008-01-05
I'm currently doing an OU course and part of the software I need requires JMF installed. The OU told me that they don't support Linux so if I want to get it working I have to do it myself else use Windows...

Anyway, I downloaded a .bin installer for the framework and ran it. Everything seemed ok but the course software gave the error

Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/ControllerListener
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
        at calshell.Main.<init>(Main.java:49)
        at calshell.Main.main(Main.java:112)

I've set the environment paths as I was told to but this changes nothing. Any ideas on what I can do?

Also, now I have run and installed the JMF using the .bin, how can I uninstall it? There is no uninstaller in the created directory and rearunning the .bin just tries to write over what was there, offering no uninstall.

Thanks in advance.

---

### Post by spydon on 2008-01-05
Check this link out: [http://ubuntuforums.org/showthread.php?p=646042](http://ubuntuforums.org/showthread.php?p=646042)
I have never used JMF so I can't help you more then that :(.

---

### Post by JayeD on 2008-01-05
Yeah, that's what I had already found and tried to no avail :(

---

