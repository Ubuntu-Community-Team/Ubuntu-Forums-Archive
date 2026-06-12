---
title: "No JDK found on this system..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by paperBag on 2007-08-05
Not realizing that the Java 6 SDK and NetBeans 5.5 were available in Synaptic (I'm very to to Linux, Ubuntu especially), I downloaded and installed them manually from the Java Sun site. Now I want to UNinstall them, and am having some problems. When I try to remove NetBeans, I get the "No Java Development Kit (JDK) was found on this system" message. Their installation paths are as follows:
```
/home/tcords/jdk1.6.0_02
/home/tcords/netbeans-5.5.1
```

I tried using both:```
-is:javahome /home/tcords/jdk1.6.0_02/jre/bin/java
-is:javahome /home/tcords/jdk1.6.0_02/bin/java 
``` to tell it where the jdk was installed, but it just quits without even looking for java. Any ideas?

I read similar posts and also tried ```
sudo update-alternatives --config java
``` and chose Java 6, but that didn't work either.

---

### Post by Happy_Man on 2007-08-05
> **paperBag said:**
> Not realizing that the Java 6 SDK and NetBeans 5.5 were available in Synaptic (I'm very to to Linux, Ubuntu especially), I downloaded and installed them manually from the Java Sun site. Now I want to UNinstall them, and am having some problems. When I try to remove NetBeans, I get the "No Java Development Kit (JDK) was found on this system" message. Their installation paths are as follows:
```
/home/tcords/jdk1.6.0_02
/home/tcords/netbeans-5.5.1
```

I tried using both:```
-is:javahome /home/tcords/jdk1.6.0_02/jre/bin/java
-is:javahome /home/tcords/jdk1.6.0_02/bin/java 
``` to tell it where the jdk was installed, but it just quits without even looking for java. Any ideas?

I read similar posts and also tried ```
sudo update-alternatives --config java
``` and chose Java 6, but that didn't work either.
I dunno.... just try deleting those folders in /home. That should do it.

---

### Post by apswartz on 2007-08-05
If the Sun installer doesn't provide an uninstaller, then you can probably just safely delete the directory containing the installation.

Then install it from the repositories and the new settings and environment should be saved.

Disclaimer: I do not use JDK or Netbeans

---

### Post by paperBag on 2007-08-06
I was just going to remove the directories, but they both came with Uninstallers, so I don't know if that's going to cause me problems later. The part listed earlier:
```
-is:javahome /home/tcords/jdk1.6.0_02/jre/bin/java
-is:javahome /home/tcords/jdk1.6.0_02/bin/java
``` were arguments TO the uninstaller, so more completely:```
-is:javahome /home/tcords/jdk1.6.0_02/jre/bin/java
-is:javahome /home/tcords/jdk1.6.0_02/bin/java
``` I'm going to look through  the install log to see what exactly the installer did, and post any updated information in case someone else ever has this problem.

---

### Post by kojiro on 2007-12-09
I had the same problem in Debian. My solution was the following:

```
sudo export JAVA_HOME=jvm_dir
```

in my case it was:

```
sudo export JAVA_HOME=/usr/lib/jvm/java6-sun
```

in your case i think it is

```
sudo export JAVA_HOME=/home/tcords/jdk1.6.0_02
```

after that, and to see if it worked, you can use
```
echo ${JAVA_HOME}
```
and that should print the exported dir.

Now try to run the uninstaller by
```
sudo ./uninstaller
```

---

