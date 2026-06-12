---
title: "Javac Compiler"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-10
Hey. How can I get the Javac command in my terminal?

---

### Post by theRightNee on 2008-01-10
[http://ubuntuforums.org/showthread.php?t=142091](http://ubuntuforums.org/showthread.php?t=142091)

hope this helps

---

### Post by jordank on 2008-01-17
I read the above links and tutorials, but I'm not sure which version of java i should get. I went to the java homepage, and saw that there are a ton of different types of javas.  If I wanted to be able to make and compile simple java programs (for school), what version might I want to get? 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter)

That's where i ended up, some java 6 update.  I don't know anything about java, so i dont know which version does what.  Any guidance on this would be greatly appreciated.  Also,  I'm running 64 bit linux.

---

### Post by jordank on 2008-01-17
hrmm. sorry that link doesn't appear to work, but regardless, what version of java should i be getting?

---

### Post by SOULRiDER on 2008-01-17
6
```
sudo aptitude install sun-java6-jdk
```

---

### Post by jordank on 2008-01-17
i typed that, but i want the java compiler. 

For example: javac Testprogram.java

i want to compile that.

but when i type javac in my terminal now:

jordan@Jorcomp:~$ javac
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

---

### Post by jordank on 2008-01-17
In synaptic, i searched "java 6" and got a list of different java packages i may download.  If i want the java compiler, (javac) which would i download?

---

### Post by SOULRiDER on 2008-01-17
You want the JDK, you can install it by doing
```
sudo aptitude install sun-java6-jdk
```

---

### Post by jordank on 2008-01-17
This didn't work, however i did get it working.

For my 64 bit, java 6 did not work.  To get around this I installed the java 5 JDK (java development kit) from synaptic.
After installing the java 6 jdk, my directory path was sent to the java 6 folder, which needed to be fixed to account for the new java 5 jdk i downloaded.  I had to change my path to the javac of the java 5 jdk.

---

### Post by SOULRiDER on 2008-01-17
Good thing you got it working. I dont see why java6 isnt working on your computer, even if its using a 64bit processor.

---

