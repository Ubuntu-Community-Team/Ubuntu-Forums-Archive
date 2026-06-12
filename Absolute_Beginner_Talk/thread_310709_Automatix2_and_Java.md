---
title: "Automatix2 and Java"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-12-01
Hey guys, I'm using ubuntu 6.10 and I just installed automatix2 in the aim to install Sun Java 1.5 JRE which I did.

It seems this has had no affect as the sites needing java still say to install java, is there something else I need to install for the plug in?

Thanks in advance.

---

### Post by nickburns on 2006-12-01
Ubuntu has jre in one of the repos:

sudo apt-get install sun-java5-jre

or 

sudo apt-get install sun-java5-jdk

for java for web, install the firefox plugin to get it to work.

---

### Post by J0E0NE on 2006-12-01
> **nickburns said:**
> Ubuntu has jre in one of the repos:

sudo apt-get install sun-java5-jre

or 

sudo apt-get install sun-java5-jdk

for java for web, install the firefox plugin to get it to work.

Yup ok just ran those two commands, that got 2 things installed how do I install the FF plugin please?

---

### Post by dwblas on 2006-12-01
Automatix should have installed that for you.  Check to see that you have a java link in /usr/bin to /usr/lib/jvm/java...blah/jre/bin/java

---

### Post by arnieboy on 2006-12-01
> **J0E0NE said:**
> Hey guys, I'm using ubuntu 6.10 and I just installed automatix2 in the aim to install Sun Java 1.5 JRE which I did.

It seems this has had no affect as the sites needing java still say to install java, is there something else I need to install for the plug in?

Thanks in advance.

are you running ubuntu amd64 edition?

---

### Post by esaym on 2006-12-01
Make sure you have a sym link in your firefox plugins directory to /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

that file has to be linked.  you can't copy the whole file into the plugin directory like some of the other plugings :)

---

### Post by J0E0NE on 2006-12-02
> **arnieboy said:**
> are you running ubuntu amd64 edition?

Yes I am, what does it change?

---

### Post by J0E0NE on 2006-12-02
That's interesting, I just installed swiftfox which is aparently optimised for my amd 64 bit system.
Automatix installed it for me and it works but it also installed the plugins etc... and when I go on a site needing java I still dont have the available plugin.

Lol I'm a bit lost

---

### Post by J0E0NE on 2006-12-02
No one can help me?
Automatix2 has installed swiftfox and the commonly used swiftfox plugins like java and flash yet when I go on a site that needs them it the site says I dont have the plugin....

Is there something I need to do to activate them?

Thanks in advance.
Joe

---

### Post by Ocxic on 2006-12-02
"sudo update-alternatives --config java"
and select the new sun java

---

### Post by arnieboy on 2006-12-02
> **J0E0NE said:**
> Yes I am, what does it change?

there is no java plugin for amd64 firefox. 
You can install 32 bit swiftfox and its plugins to get java support on swiftfox.

---

### Post by dwblas on 2006-12-02
> sudo update-alternatives --config javaIf this doesn't work, you are going to have to create a symlink to /usr/bin/java yourself. Or adding /usr/lib/jvm/..... to your path might also work.  Java is installed but Firefox can't find it.

---

### Post by slicker on 2006-12-02
> **arnieboy said:**
> there is no java plugin for amd64 firefox. 
You can install 32 bit swiftfox and its plugins to get java support on swiftfox.

Why does automatix install non free software like swiftfox?

---

### Post by J0E0NE on 2006-12-02
Thanks very much that sorted it m8 :mrgreen:

---

