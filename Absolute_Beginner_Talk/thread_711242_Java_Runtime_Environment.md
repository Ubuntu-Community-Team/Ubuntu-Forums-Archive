---
title: "Java Runtime Environment"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by OliH on 2008-02-29
Hi,

I'm having problems installing Java Runtime Environment. I've tried downloading it from the java website and installing it, and also typing the command:

sudo apt-get install sun-java5-jre sun-java5-plugin

However, when I try to use Macros with OpenOffice, it tells me that JRE is not installed. Also, when I test whether java is installed on Firefox, it tells me to install additional plugins (Java plugins) which I do, but then it still tells me to install them when I test it again, even after I have restarted firefox.

I'm running Firefox 3 Beta 3 and Ubuntu 8.04 installed using wubi.

Thanks in advance,

Oli

---

### Post by taurus on 2008-02-29
What is the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by hoo2 on 2008-02-29
I have the same problem but i also get the following msg 

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.

i'm runing kubuntu 7.10 gusty

---

### Post by taurus on 2008-02-29
> **hoo2 said:**
> I have the same problem but i also get the following msg 

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.

i'm runing kubuntu 7.10 gusty

You need to install sun java first.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by OliH on 2008-03-01
Hi,

Thanks for your reply. Then I enter the command, I get:

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
```

When I type the command "java - version" I get:

```
java version "1.4.2_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_05-b04)
Java HotSpot(TM) Client VM (build 1.4.2_05-b04, mixed mode)
```

Does this mean that JRE is installed correctly?

Oli

---

