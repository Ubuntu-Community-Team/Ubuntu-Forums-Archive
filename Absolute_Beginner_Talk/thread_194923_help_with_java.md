---
title: "help with java"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by x3non on 2006-06-12
Hi all,

i was using breezy then i dist-upgraded to dapper.

So i installed sun java from multiverse repo, but everytime i try running a java app i get this error:


Error: cannot find Java Runtime (JRE).
       please set the environment variable JAVA_DIR to the base dir
       where the JRE is installed.
       default JAVA_DIR=/opt/OV/jre/jre1.4


can anyone help me?

tnx!

---

### Post by Perfect Storm on 2006-06-12
You might want to uninstall java. It seems the distro upgrade mess a little bit up. Also get java sun 1.5 instead of 1.4 blackdown.

---

### Post by x3non on 2006-06-12
i already removed blackdown java and reinstalled sun with no luck

---

### Post by Perfect Storm on 2006-06-12
Try with:
```
sudo update-alternatives --config java
```

and choose java sun j2re 1.5

---

### Post by jvictor on 2006-06-12
I am bit amused by JAVA_DIR .. usually apps ask for JAVA_HOME

However you can set it in ur ~/.bashrc file like this


Add these to the end of the file

JAVA_DIR=<top_level_dir_of_java>
export JAVA_DIR

eg: 

JAVA_DIR=/usr/lib/jvm/java-1.5.0-sun
export JAVA_DIR


Also, u need to be sure where u have installed the sun JDK. for me it was under /usr/lib/jvm/java-1.5.0-sun in dapper.


close the shell re-open and try executing ur pgm

also we'd like to see the output of

java -version

---

### Post by elemental666 on 2006-06-12
just a word of caution, don't install the JDK unless your planning to develop java apps.  install JRE (just the run time environment).

I find its easier to do this in synaptic as doing it from the command line doesn't always display the User Agreement (might just be me tho)

1st install sun-java5-bin in synaptic, and accept the user agreement.
2nd set your default JVM per: [https://wiki.ubuntu.com/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://wiki.ubuntu.com/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

---

### Post by jvictor on 2006-06-12
> just a word of caution, don't install the JDK unless your planning to develop java apps. install JRE (just the run time environment).

Oh yes ! I'm a java developer so my default thought is the JDK way .. sorry for that

---

### Post by x3non on 2006-06-12
[QUOTE=jvictor]I am bit amused by JAVA_DIR .. usually apps ask for JAVA_HOME

However you can set it in ur ~/.bashrc file like this


Add these to the end of the file

JAVA_DIR=<top_level_dir_of_java>
export JAVA_DIR

eg: 

JAVA_DIR=/usr/lib/jvm/java-1.5.0-sun
export JAVA_DIR


Also, u need to be sure where u have installed the sun JDK. for me it was under /usr/lib/jvm/java-1.5.0-sun in dapper.


close the shell re-open and try executing ur pgm

also we'd like to see the output of

java -version[/QUOTE]



thanks...it worked! :D

---

### Post by elemental666 on 2006-06-12
[QUOTE=jvictor]Oh yes ! I'm a java developer so my default thought is the JDK way .. sorry for that[/QUOTE]

[QUOTE=x3non]thanks...it worked! :D[/QUOTE]

groovy x2!

---

