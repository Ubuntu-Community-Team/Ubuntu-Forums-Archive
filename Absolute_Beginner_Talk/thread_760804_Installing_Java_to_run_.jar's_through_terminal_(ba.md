---
title: "Installing Java to run .jar's through terminal? (bash)"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by linkmaster03 on 2008-04-20
Running all commands starting with "java" shows this exact thing:

```
brad@brad-laptop-ubuntu:~$ java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
brad@brad-laptop-ubuntu:~$ 

```

---

### Post by Mark20 on 2008-04-20
```
java -jar yourJarFile.jar
```

---

### Post by y-lee on 2008-04-20
It looks like you do not have [Java installed]("https://help.ubuntu.com/community/Java"). 

If java is installed post back something else is wrong :confused:

---

### Post by linkmaster03 on 2008-04-20
I have Java installed. I have tried reinstalling it and the same thing happens in terminal.

---

### Post by linkmaster03 on 2008-04-20
I had uninstalled IcedTea, and I found that's where the command was pointing to. I reinstalled IcedTea and it works now. :)

---

