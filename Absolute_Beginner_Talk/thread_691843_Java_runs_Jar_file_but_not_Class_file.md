---
title: "Java runs Jar file but not Class file"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Ultros88 on 2008-02-09
Hello All. Just starting to program Java in Ubuntu. I'm using the NetBeans IDE, but I'd also like to be able to use the terminal properly for compilation and execution. In any case... my HelloWorld example runs out of NetBeans, and when I use: > java -jar helloworld.jar

Now, it is my understanding that I ought to be able to use the 'java' command similarly with the helloworld.class file. I've read everything I could find relating to people's situations with similar problems and I assume that there is some problem with the CLASSPATH.

Here is the error message:
Exception in thread "main" java.lang.NoClassDefFoundError:
Main (wrong name: helloworldapp/Main)
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

I've fiddled around with defining the path to my java directory by editing /etc/environment and ~/.bashrc, but for the life of me cannot seem to get '> java HelloWorld' to run. I am running this command out of the directory where the .class file is located.

Any help would be much appreciated.
Thanks,
Ultros88

---

### Post by inksmithy on 2008-02-09
prett simple really, when you run the project in netbeans, netbeans compiles the program and uses it from a temporary location.

When you want to run it from the command line, you need to compile it yourself.

Try 'javac HelloWorld' in the directory that the class lives in and then try 'java HelloWorld'. Your mileage may differ, but no matter what happens, you will need to compile it, unless you have already compiled it as a package within netbeans and you are attempting to run the compiled program from netbeans.

---

### Post by Ultros88 on 2008-02-09
Thanks, I tried what you suggested. Compiling in the directory with HelloWorldApp.java, and then running that .class file that it creates works. However, I still cannot run the .class file produced by NetBeans. You said that this has something to do with there being temporary files. How does that work and why would it affect my being able to run a NetBeans produced .class file from the command line? A response would be great, although primarily for my own edification rather than solving the problem I initially posted about. If I need to run from the command line I'll just compile the .class files myself.

Thanks again,
Ultros:)

---

