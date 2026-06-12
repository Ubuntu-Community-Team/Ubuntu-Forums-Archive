---
title: "Installing Java+NetBeans?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Nahum&#1459; on 2007-04-28
I got the file jdk-6u1-nb-5_5-linux-ml.bin from java.sun.com

what to do?

---

### Post by loell on 2007-04-28
in the terminal
```
sudo apt-get install  netbeans5.5
```

---

### Post by larry wales on 2007-05-06
hi,

I got the file netbeans-6.0m9-full-linux.sh 

I tried running:  

sudo apt-get install  netbeans6.0

and got the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package netbeans6.0

What should I do?

thanks, 

-larry

---

### Post by zvacet on 2007-05-06
If you have all repositories open then you have netbeans in synaptic.And Java too,of course.

---

### Post by larry wales on 2007-05-06
thanks for replying!  However, I checked Synaptic and NetBeans 6.0 milestone 9 isn't yet available.

I therefore downloaded the file from netbeans.org, and when I try to run it, I get the following output:

[INDENT]Configuring installer...
Search JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.
[/INDENT]

However, I already installed the Sun Java 1.6 JDK on my system through Automatix.

Any ideas would be MUCH appreciated.  How, for example, can I verify the location of JDK?

thanks,

-larry

---

### Post by johann_p on 2007-05-06
> **larry wales said:**
> However, I already installed the Sun Java 1.6 JDK on my system through Automatix.

Any ideas would be MUCH appreciated.  How, for example, can I verify the location of JDK?


I dont know how Automatix installs JDK - if it uses a package or does a binary download/install. If it uses a package, try to find the JDK package in the synaptic package list and click on the files tab to see where everything is installed.

Or if it was installed from the original Sun binary install package do
  ls -l `which javac`
end follow any symbolic links until you get to the directory that contains bin/javac, which should be the directory you want.

---

