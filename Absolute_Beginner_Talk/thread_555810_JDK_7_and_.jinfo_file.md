---
title: "JDK 7 and .jinfo file"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by serid on 2007-09-20
Hi everyone !

Just wondering, whether anybody has got a .jinfo file for JDK 7 platform ...
I need it to use update-java-alternatives to set JDK 7 as a default JDK.
Also, is there another way of setting it up as a default JDK ? Where is
this all information about JDK, JRE and other java stuff  written ?

Cheers,

Adrian

---

### Post by Diabolis on 2007-10-16
Just put the location of your installation at the beginning of your path. Your pc will always use the first occurrence of a java installation declared in your path. You still can write java applications under a specific jdk version by setting it up through a ide like netbeans or eclipse.

In my opinion the easiest way of doing this is by modyfing your path variable in your .bashrc file, it is in your home directory. I added this lines in my .bashrc file:
```
# User specific environment and startup programs
JAVAHOME=/home/gaston/jdk1.6.0_02/bin
PATH=$JAVAHOME:$PATH:
```

You can check if it worked by typing this in the terminal:
```
java -version
echo $JAVAHOME
```

JAVAHOME is the name I gave to this variable, you can change to whatever you want.

---

### Post by serid on 2007-10-17
Thanks ofr the tip !

Adrian

---

