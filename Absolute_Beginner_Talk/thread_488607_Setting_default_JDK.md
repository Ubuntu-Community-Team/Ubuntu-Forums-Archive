---
title: "Setting default JDK"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2007-06-30
Hi,

I installed the latest version of Java, which is located in */usr/lib/jvm/java-6-sun-1.6.0.00*.

Now I want to set Ubuntu's default Java to this version, however, when I try *sudo update-alternatives --config java* it is not listed there.

Is there a file I can add */usr/lib/jvm/java-6-sun-1.6.0.00* to which will make it show up when I run the *update-alternatives* command, consequently making Ubuntu's default Java that one?

Regards.

---

### Post by nereid on 2007-06-30
Use *update-java-alternatives*.

---

### Post by jpangamarca on 2008-01-28
All the tutorials and howtos I've found on the Internet haven't worked for me, they install it first via apt-get. I don't have a fast Internet connection to install via apt-get, so I installed JDK from a .sh installer (jdk-6-linux-i586.bin, from Sun) that someone gave to me, I made it uncompress all the files to /usr/lib/jvm/jdk1.6.0. How do I set *that* JDK as the default JDK? When I issue "java" to the CLI, I get this:

```
comp@ubuntu-desktop:~$ java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
```

It's obvious it's using the GNU JDK, but need Sun Java in order to install NetBeans; when I try to install it ($ sudo sh netbeans-5_5-linux.bin) I get a message "No Java Development Kit(JDK) was found on this system."

I already edited /etc/jvm, it looks like this:

```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/jdk1.6.0
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr
```

If someone can help me with this, I'd be really grateful.

---

