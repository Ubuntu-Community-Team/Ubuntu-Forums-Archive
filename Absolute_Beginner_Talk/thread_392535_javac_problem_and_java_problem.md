---
title: "javac problem and java problem"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-03-24
It seems I was finally able to install javac but the compiler is still giving me problems. I followed the following steps in order to install javac

I added the following two links to my repositories.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

After this have apt updates its repository

sudo apt-get update

And finally, just tell it to install java :)

sudo apt-get install sun-java5-jd
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

After this have apt updates its repository

sudo apt-get update

And finally, just tell it to install java :)

sudo apt-get install sun-java5-jdk

But whenever I try to compile a file called Testing.java which is the main class for a group of 4 classes, it always gives me this error.


home@home-desktop:~/Desktop$ javac Testing.java
home@home-desktop:~/Desktop$ java Testing


Exception in thread "main" java.lang.UnsupportedClassVersionError: Testing (Unsupported major.minor version 49.0)
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
home@jhome-desktop:~/Desktop$ 



I would greatly appreciate if you could tell me what I need to fix in order that javac work all the time for me. Thank you very much.


:guitar: 

:lolflag:

---

### Post by Mister.Vash on 2007-03-25
It might not be using the version of Java that you just installed. To verify the version that you are using type in "[COLOR="Navy"][FONT="Fixedsys"]java -version[/FONT][/COLOR]"   which will list the version that that you are currently using
```

~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

```

If it is not what you expect to see, then run "[COLOR="Navy"][FONT="Lucida Sans Unicode"]sudo update-alternatives --config java[/FONT][/COLOR]"
```

~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

Which will display the list of what is available and you can then select what you want as your default

---

### Post by BryanFRitt on 2008-01-27
using
sudo update-alternatives --config java
and
sudo update-alternatives --config javac
helped fix my problem
...pick some combination that works...

---

### Post by sib13 on 2008-03-05
i had a similar problem and this helped. thanks guys!!

:guitar:

---

