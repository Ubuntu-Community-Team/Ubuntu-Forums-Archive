---
title: "problem with java"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by jenny_psion on 2007-04-01
Hello, 

I have just installed a program that uses java. I have also installed jre 1.5 from the java sun webpage, but I still get an error message. I think maybe the jre is not installed properly. 
is it possible to check whether i have installed the jre properly?
the error messages i get are something like that:
```

could not execute parser.
be sure java 1.5 (or newer) is installed.
error: exception in thread "main"
java.lang.UnsupportedClassVersion ......

```

Thanks in advance.
psion.

---

### Post by jenny_psion on 2007-04-01
PS:

I did the following, which I have read in one of the threads in this forum:

```

jen@portableTyke:~$ which java
/usr/bin/java
jen@portableTyke:~$ 

```

So, I assume that I have installed Java correctly... but why do I get this error message when I try to load my program?

Thanks, 
psion.

---

### Post by h0ax on 2007-04-01
Are you using a command line java compiler or a GUI?


Try 
> 
java -version


---

### Post by jenny_psion on 2007-04-01
Thank you. 
Hmmm, this is interesting. It says that I am not using version 1.5 ... but that's the version I downloaded and installed from the java webpage. How weird.

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
jen@portableTyke:~$ 

```

How can I get version 1.5 using "apt-get" or so?

The program I am using that needs java is a GUI program.

psion.

---

### Post by h0ax on 2007-04-01
Glad to help - I installed eclipse (a nice Java frontend GUI)
via the command 
> sudo apt-get install eclipse


since you already have 1.4 installed try
> sudo apt-get upgrade java

---

### Post by jenny_psion on 2007-04-01
Hi, 

I have just done that "upgrade java", however, I still seem to have version 1.4.2 on my computer:

```
jen@portableTyke:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

Is there any other way I can update?

Oh, I also just checked in "Adept Manager" and I can see that it says JRE 5.0 is installed. Hmmm, this is strange. How come my computer doesn't recognise that?

Thanks, 
psion.

---

### Post by h0ax on 2007-04-01
Maybe you could try removing it and then just doing an install from apt-get ?

sudo apt-get remove java
sudo apt-get install java

We've determined your issue is an older version of the java libraries, but I'm sorry I'm not so much help getting the updates, hehe.

---

### Post by jenny_psion on 2007-04-01
Hmmm, now it says that it cannot find java.

```
root@portableTyke:/usr/java# apt-get remove java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package java

```

Strange...

---

### Post by jenny_psion on 2007-04-01
Yay!!! It works.

Just to close this thread... this is how I changed to version 1.5:

```
root@portableTyke:/usr/java# update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+        3    /usr/lib/j2se/1.4/bin/java
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
root@portableTyke:/usr/java# version -java
bash: version: command not found
root@portableTyke:/usr/java# java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
root@portableTyke:/usr/java# 

```

Thanks, 
psion.

---

### Post by Sef on 2007-04-01
> Maybe you could try removing it and then just doing an install from apt-get ?

sudo apt-get remove java
sudo apt-get install java


That works only if you install via apt-get, aptitude, or synaptic.   If installing with the command line use 'sudo aptitude  install package-name'.  Aptitude will remove all the depencies that were installed.  Apt-get will not.

The easy way to get java is this way:  Applications > Add/Remove > Search > Sun Java 5.0 > click on both boxes > ok > click a couple of more times when asked.   (Note: See [Java Help]("https://help.ubuntu.com/community/Java"), if you don't see Java after a search.)

---

### Post by jenny_psion on 2007-04-01
I agree, that way is easiest... but as I had different versions of Java installed, I had to select one of them... and then it worked.

---

### Post by h0ax on 2007-04-01
> **Sef said:**
> That works only if you install via apt-get, aptitude, or synaptic.   If installing with the command line use 'sudo aptitude  install package-name'.  Aptitude will remove all the depencies that were installed.  Apt-get will not.

The easy way to get java is this way:  Applications > Add/Remove > Search > Sun Java 5.0 > click on both boxes > ok > click a couple of more times when asked.   (Note: See [Java Help]("https://help.ubuntu.com/community/Java"), if you don't see Java after a search.)

Thank you for the tip, glad you got yourself all fixed up psion.

---

