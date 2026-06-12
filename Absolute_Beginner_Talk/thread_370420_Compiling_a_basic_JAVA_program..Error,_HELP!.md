---
title: "Compiling a basic JAVA program..Error, HELP!"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Nectron on 2007-02-25
Hey All,

I'm trying to compile a small java program I've written for my java class, but the compiler is giving me an error and I don't really know what it is.. I'm sure the program is correct but I'm guessing I'm mising some libraries.

```

nectron@nectron-laptop:~/Desktop$ java Amer.java
Exception in thread "main" java.lang.NoClassDefFoundError: Amer.java
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: Amer.java not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

If I'm missing libraries, how to obtain them?

Thanks in advance..

---

### Post by steve.horsley on 2007-02-25
You need to compile the file first. I assume that the source code (Amer.java) is on your desktopm and this is you current working directory (as it was above). 
First, compile with javac (not java):
**javac Amer.java**
then run it with java, but don't give the .class extension:
**java Amer**

---

### Post by jordanmthomas on 2007-02-25
Also, you are using gcj (which kind of sucks)
Try looking around Synaptic for the real jdk.  You'll have a LOT less problems.

---

### Post by Nectron on 2007-02-26
I've checked the Synaptic Package Manager and found a "free-java-sdk"

I've installed it with other required dependencies..

How can I run this?! It doesn't appear on the menu, and I tried googling that but couldn't find how to run it..

The command line compiling (java prog.java/java prog) and that works..

I still need to know how to run the free-java-sdk, is it in GUI ?

---

### Post by steve.horsley on 2007-02-26
You did run it. It consists of a set of command-line tools, the ones you will use most are **javac** the compiler and **java** the runtime interpreter.

However, can I suggest that you consider installing the Sun java SDK (it's in the repositories) and also get Suns SDK documentation and also their java tutorial. The docs and tutorial are available from java.sun.com. I would say that both are essential.

If you want a gui, a nice easy starter is a package called bluej, [www.bluej.org](www.bluej.org).

---

### Post by neo_reloaded on 2007-03-19
> **Nectron said:**
> Hey All,

I'm trying to compile a small java program I've written for my java class, but the compiler is giving me an error and I don't really know what it is.. I'm sure the program is correct but I'm guessing I'm mising some libraries.

```

nectron@nectron-laptop:~/Desktop$ java Amer.java
Exception in thread "main" java.lang.NoClassDefFoundError: Amer.java
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: Amer.java not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

If I'm missing libraries, how to obtain them?

Thanks in advance..

The command that you have used to compile is incorrect.
This is not Java related forum, but here is how to compile a java program.
The command is "javac"

so you should be doing
javac Amer.java

then it will create Amer.class in the working directory.

Set your classpath to include present directory. For example, type the following:

export CLASSPATH=.:$CLASSPATH 

Note: It is a dot "." followed by colon ":" and then $CLASSPATH.
now, type. 
java Amer

This should run your main method. Also, GCJ is the default java and javac in Ubuntu. If you want to override it with Sun's jdk - follow my post here. 
[http://rchandran.blogspot.com/2006_12_01_archive.html](http://rchandran.blogspot.com/2006_12_01_archive.html)

HTH

---

