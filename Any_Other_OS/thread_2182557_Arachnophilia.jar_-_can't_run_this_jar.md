---
title: "Arachnophilia.jar - can't run this jar"
date: 2013-10-21
forum: Any Other OS
---

### Post by Socman on 2013-10-21
All research and searches to no avail.  The problem:

Installed:
Mint 13 Maya (based on Ubuntu 12.04)
Icetea-7-Plugin (Version: 1.2.3-0ubuntu0.12.04.3)
Openjdk-7-jre (Version: 7u25-2.3.10-1ubuntu0.12.04.2)

According  to Arachnophilia, java must be installed BEFORE downloading and running  Arachnophilia.jar.    This was done, as follows:

1.  Icedtea plugin and Openjdk runtime were both first installed.
2.  Terminal "java -version" returns:[INDENT]java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.6) (6b27-1.12.6-1ubuntu0.12.04.2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
[/INDENT]

3.  Latest Arachnophilia.jar was downloaded into a folder "Arachnophilia" on my desktop.
4.   According to Arachnophilia, to run Arachnophilia.jar I used the  terminal, went into the Arachnophilia folder and attempted to run  Arachnophilia.jar as per directions by running "java -jar  Arachnophilia.jar".

The return:[INDENT]computer@computer ~/Desktop/Arachnophilia $ java -jar Arachnophilia.jar
Exception  in thread "main" java.lang.UnsupportedClassVersionError:  Arachnophilia/Arachnophilia : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: Arachnophilia.Arachnophilia. Program will exit.
[/INDENT]

I'm stumped, any ideas?      Thanks...

---

### Post by holycow131415 on 2013-10-21
You will probably need to install oracle java, not openjdk. Search the forums here on how to install a oracle java ppa to make your life easier, I know i've seen instructions on these boards somewhere.

---

### Post by Lars Noodén on 2013-10-22
It would be nice if the editor were packaged so it could be installed from the Software Center or Synaptic:

[https://bugs.launchpad.net/ubuntu/+bug/263560](https://bugs.launchpad.net/ubuntu/+bug/263560)

It's an old bug an unlikely to go anywhere but you can still add your "me, too" to it.

---

### Post by Socman on 2013-10-22
For now it appears that Openjdk doesn't work with Arachnophilia, so the task now is to install Oracle/Sun Java 1.7 using either a manual install, or perhaps better from an updatable repository at WebUpD8.org.    The latter seems the easiest, requires only 3 short commands to achieve both installation, and allegedly makes for easy updates and/or deinstallation.

I will try it, and report back..

---

### Post by Socman on 2013-10-22
[SOLVED]

OK good people, I found what has to be the easiest and quickest solution ever.   Here's what I did:

1.  Removed Icedtea plug-in and then Openjdk jre, in that order.

2.  Went to Webupd8: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) 
opened my terminal and entered the following three commands, in order, one at a time:

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

You will be asked to confirm a couple of times, do so.  You will also be asked to "agree" to the license, and you will.

3. That's it.  I confirmed the version ("java -version"), and noted that the latest java 1.7 was indeed installed. 
I stopped right there and did NOT update, nor did I set the defaults, as Webupd8 would have you do.

4. At this point I exited terminal, went to Arachnophilia.jar, right-clicked and opened it with "Open with Oracle Java runtime".

It worked perfectly, and I'm a happy bear.  


*******
Special Note:  I found that it was important to remove IcedTea plugin first, then Openjdk jre second,
as this is the same order as installed (I had installed Icedtea, which seems to install Openjdk), then restarted. 
I found that Icedtea remained as an add-on in Firefox and T-bird, even though removed.

This latter was solved when after installing Oracle Sun Java per above, I checked again and now Fox and T'bird properly
show "Java(TM) Plugin 10.45.2", along with a warning "known to be vulnerable".  I set this plug-in to "never active" 
as I choose not use java in my browser or email.

Bottom Line:  this is a super easy solution, I get java to run my java apps, but disable it in Fox and T-bird, 
and unlike the complicated manual install, Webupd8 makes installing, updating and uninstalling downright simple and fast,
no worries whatever.

---

### Post by PeterRJG on 2013-10-23
Thanks for this. This indirectly solved a problem I had with Blackboard Collaborate (an education app) not working with IcedTea. Looks like it, and many other things, are Oracle Java only.

---

### Post by kostkon on 2013-10-24
> **Peter1968 said:**
> Thanks for this. This indirectly solved a problem I had with Blackboard Collaborate (an education app) not working with IcedTea. Looks like it, and many other things, are Oracle Java only.
Not true in this case. I just tested it and it works just fine with OpenJDK 7. You can install OpenJDK 7 from the repos (using the softwre centre, apt-get etc.), i.e. there are two versions of it available, 6 and 7.

---

### Post by PeterRJG on 2013-10-24
Hmm, I kept getting a list of downloaded jar files when I tried to open Collaborate with OpenJDK. I should've taken a screenie of it to show what I mean. But yeah, it was most likely version 6. Ah well, it's running fine now with Oracle Java.

---

