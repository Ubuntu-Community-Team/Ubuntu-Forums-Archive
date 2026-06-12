---
title: "[SOLVED] java jdk not working"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by jamesjeffries1 on 2008-04-16
i have recently upgraded my version of ubuntu to 710. at the same time i have updated my jdk from 1.5 to 1.6. Now it doesnt work. I have installed the right packages using apt-get(sun-java6-jre,sun-java6-jdk,sun-java6-plugins etc.) i've updated the environment variables but all no use. java works and is the correct version.

In the usr/lib/jvm/java-6-sun/bin folder the java icon is an executable icon with an arrow above it and to the right, however the javac one doesnt, so i think that this could be the problem but i dont know what this means.

Any ideas would be most welcome
Thanks

---

### Post by Inxsible on 2008-04-16
in a terminal```
java -version
``` That should show you the default JRE on your system. Check if that is pointing to 1.6 or still pointing to 1.5

---

### Post by jamesjeffries1 on 2008-04-17
$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

the java commend works fine. its javac that doesnt:
$ javac
The program 'javac' can be found in the following packages:
 * gcj-4.1
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * jikes-classpath
 * ecj
 * j2sdk1.4
 * jikes-gij
 * jikes-kaffe
 * sun-java5-jdk
 * java-gcj-compat-dev
Try: sudo apt-get install <selected package>
bash: javac: command not found

I have also tried this which has been sugested in other threads:
$ sudo update-alternatives --config javac

There is only 1 program which provides javac
(/usr/lib/jvm/java-6-sun/bin/javac). Nothing to configure.

---

### Post by jamesjeffries1 on 2008-04-17
ok managed to fix it using this command if anyones interested
sudo update-java-alternatives --set java-6-sun

---

