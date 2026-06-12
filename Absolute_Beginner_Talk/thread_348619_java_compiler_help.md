---
title: "java compiler help"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by FANGBIN on 2007-01-29
hi everyone,

i wrote some java programs, and i want to compile and run in ubuntu.
i already install the J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox
but when i use javac, i got the following message:
bash: javac: command not found



can anyone help me out
thanks

---

### Post by mcglnx on 2007-01-29
Is Java install?
Normally you can find it using the command line prompt.
Try:
  $ java -help
  $ which java
 or 
  $ locate java

If not found, try to install java using synaptic.
Notes: you need the JSDK and not the JRE to compile. JRE is only the runtime - not the development kit.

HTH,
M

---

### Post by jordanmthomas on 2007-01-29
JRE is not the same as the JDK, which you will need to install.

---

### Post by mcglnx on 2007-01-29
:) may be I was not clear enough :)

---

### Post by jordanmthomas on 2007-01-29
> **mcglnx said:**
> :) may be I was not clear enough :)

...that was the one line of your post I didn't read.  :o

---

### Post by igknighted on 2007-01-29
As the previous poster mentioned, you need the JDK.  If you installed via the repositories, just search for the package sun-java5-jdk and install that.  It will automatically install the other packages it requires (there are 1 or 2 others i believe).  If you want the very latest version of java, check on java.sun.com, find the download for the Java SE version 6 JDK and follow sun's install instructions.  This will require a little command line manipulation in order to tell your system about the new java install, so as long as 1.5 is OK (until you upgrade to fiesty) i'd use the repo.

---

### Post by FANGBIN on 2007-01-29
thanks guys, i've got it work

---

### Post by dmitry on 2007-01-29
You should install java from ripository since there is official Sun Java there.

sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-fonts sun-java6-plugin

And then you'd better purge all packages connected with "gij" and "gcj" to make java command in bash run official Sun java.

---

### Post by phossal on 2007-01-29
My sig contains a link to a tutorial showing how to pull the latest Java down from Sun, and how to set it up.

---

