---
title: "How do i install a JVM"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by asimmittal on 2007-12-28
I have recently downloaded a JDK6u3 from sun's website for linux. Its a .bin file. How do I install it.

I used the same file on two versions Fiesty and Dapper.

On fiesty, I tried to run it in the terminal... everything was fine, It unpacks everything but then Nothing else happens, I see an intermediate file being created but it disappears as soon as its done.

On dapper, I ran the .bin file in the terminal again... it created a folder "jdk 1.6.0"... which is good, but then how do I set the system path to this directory. I cannot use "javac" and "java" because the shell doesnt recognize them as system commands. In windows, I could set path and classpath variables for a session. How do i do that here on ubuntu.

I dont know whats going on... please help

---

### Post by jken146 on 2007-12-28
```
sudo apt-get install sun-java6-jdk
```

You could also use Synaptic.

No need for bins.

---

### Post by asimmittal on 2007-12-28
I had downloaded an incompatible version of the JDK... I am working on a 64 bit processor and was using a 32bit compliant JDK... Such a newbie error.


Hey does anyone have a guide for using the Linux commands at the terminal...?? It would really help

---

