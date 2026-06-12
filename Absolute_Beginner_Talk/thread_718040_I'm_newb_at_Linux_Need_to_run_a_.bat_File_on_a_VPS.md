---
title: "I'm newb at Linux? Need to run a .bat File on a VPS"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Inside Sin on 2008-03-07
Hey, i'm new to the whole Linux scene, and i am into the private server business, i have a dedicated all ready up, but i don't know how to run a Windows .bat on Linux, it doesn't seem to work.

Is there something i need to do, this is the .bat(s)...

```
@echo off
title RuneJava Base Compiler.
echo Compiling all RuneJava .java Files...
cd Java
javac -d ../Server *.java
pause
```

```
@echo off
title Running Server, please wait...
cd Server
java -Xmx1024m -cp .;./jython.jar;./mysql.jar server 0
pause
```

---

### Post by Inside Sin on 2008-03-07
BUMP.

Can someone please help me.

---

### Post by drubin on 2008-03-07
Linux doesn't user .bat files, (They are windows Batch scripts).

Here is a link to Linux version of .bat files.
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


Ps, Trying to bump your thread after 30mins, Seems pointless, the same people are still sleeping, with the same people not being able to answer it being wake..

---

### Post by handydan918 on 2008-03-07
AFAIK, Windows scripts won't run on any linux box. You'll need to figure out what you are trying to do, and write a bash script to accomplish it. i don't have more than just a passing clue about bash scripting, but I know the capabilities are huge. Try googling "bash scripting" for tutorials.

---

### Post by drubin on 2008-03-07
I have never done any java work on Linux before,

But your script seems very simple and to change it to a Linux Bash file i would do.
```

1) ADD   #! /bin/bash     (this must be the first line of the file) Lets it know it is bash file
2) Remove  @echo off  (not sure what this does)
2) Remove  the title line
3) remove the last line called Pause that is a windows command 
4) Rename to  .sh 
5) give it execute permissions 
```


The other stuff should work, Not sure about the paths to where java is,

---

### Post by Inside Sin on 2008-03-07
Thanks for all the replies, i'll give it a BASH, get it?

xD

---

