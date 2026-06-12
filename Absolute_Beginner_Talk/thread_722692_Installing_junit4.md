---
title: "Installing junit4"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by uberubert on 2008-03-12
I have to use junit4 for my latest programming assignment. I've tried installing it by following the instruction given by my school group teachers, which were these:

~$ mkdir ~/javalibs/
~$ mv "path to junit-4.4.jar" ~/javalibs/
~$ echo 'export CLASSPATH="$HOME/javalibs/junit-4.4.jar:$CLASSPATH"' >> ~/.bashrc
~$ source ~/.bashrc

and to test if it works:
~$ java org.junit.runner.JUnitCore

And I get this NoClassDefFoundError, which means that the install didin''t work... (obviously)

I've made sure to type everything correctly, and the terminal gave no errors at all. (and no, I didnt type in ~$ at the beginning of every command..)

Can anyone with some experience shed some light on this? Thanks!

Oh, and I made sure that the file junit-4.4.jar is in the folder javalibs in my home/user folder.

---

### Post by Nepherte on 2008-03-12
It find it strange you still have to install. I installed Java (JRE & JDK), use eclipse and I have access to JUnit. Apart from that I don't see what you're doing wrong.

---

### Post by uberubert on 2008-03-13
I use emacs, but I'm definately changing to eclipse after this assignment is done. I have a programming-friend that talks about nothing else, hehe. I heard JUnit4 is part of eclipse, so barely any install is needed.. 

If I'm able to load up my 1 program.java file into eclipse, then maybe there is hope?

Btw, there might be a thing with the CLASSPATH, is this output supposed to mention anything about junit4? I only get one line about easyIO, like this:

~$ echo $CLASSPATH
/home/user/java/easyio/easyIO.jar:.

---

### Post by kpkeerthi on 2008-03-13
Couple of things to check
1. Check if .bashrc has the CLASSPATH you just added
2. Close and open a new terminal
If it doesn't work try ```
java -cp "$CLASSPATH:$HOME/javalibs/junit-4.4.jar" org.junit.runner.JUnitCore
```

---

