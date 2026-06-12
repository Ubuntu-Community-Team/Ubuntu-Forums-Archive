---
title: "Compile Java app"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by crazyoldman1 on 2006-06-28
I just got back from a camp that only used redhat, and they could compile a java app in the terminal by using some commands like:

1.) add jdk50
2.) javac name.java
3.) java name

are there similar commands in Ubuntu to compile a java app in terminal?

Thanks, 

Crazyoldman


when i use the javac name.java

the command works but when i try to use the 

java name command it comes back with these errors..

```

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at javax.imageio.spi.IIORegistry.<init>(libgcj.so.7)
   at javax.imageio.spi.IIORegistry.getDefaultInstance(libgcj.so.7)
   at javax.imageio.ImageIO.getRegistry(libgcj.so.7)
   at javax.imageio.ImageIO.read(libgcj.so.7)
   at javax.imageio.ImageIO.read(libgcj.so.7)
   at javax.imageio.ImageIO.read(libgcj.so.7)
   at Tilt.main(Tilt.java:12)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...7 more

```

---

### Post by LAurel on 2006-06-28
You must install the Java Development Kit.

First, you need to make sure you have the Universe repository. See _[this wiki page](https://help.ubuntu.com/community/Repositories/Ubuntu)_ for help on how to add repositories.

Then, you need to install the package called *sun-java5-jdk*. Either use Synaptic or open the terminal and type: ```
sudo apt-get install sun-java5-jdk
```

Now you can compile *.java* files with *javac* and run *.class* files with *java*.

Note: gcc can also compile *.java* files, but I prefer JDK.

---

### Post by sloggerkhan on 2007-01-16
I have this going on. I have eclipse and java installed, but when I try to run java filename from the console, it gives me a java.lang.NoClassDefFoundError even though eclipse says it runs fine. What am I missing? (Java noob)

---

