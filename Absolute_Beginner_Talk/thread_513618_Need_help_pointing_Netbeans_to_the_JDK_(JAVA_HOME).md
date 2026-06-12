---
title: "Need help pointing Netbeans to the JDK (JAVA_HOME)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by e123 on 2007-07-30
Hi all,

Thank you all for your previous posts on pointing JAVA_HOME to the JDK. I worked through those I could find and no dice. I'll explain what I've done thus far and hope that someone can help me out. Thanks in advance!

My thinkpad T41 is running Ubuntu 7.04 with all the latest patches.

I downloaded the sun 1.5 JDK using the synaptic tool. I could not find any alternatives (besides 1.6). If there is an alternative that hides less well than the sun JDK I could really use it...

I also downloaded Netbeans 5.5 with synaptic.

When I attempt to compile my code in Netbeans this error message appears:
clean:
Deleting directory /home/mdj/apps/imagej/build
compile:
Created dir: /home/mdj/apps/imagej/build
Compiling 479 source files to /home/mdj/apps/imagej/build
/home/mdj/apps/imagej/build.xml:9: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK
BUILD FAILED (total time: 0 seconds)


It warned me that JAVA_HOME was not pointing anywhere. So I attempted to follow the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME](http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME)

As best I can tell this is what JAVA_HOME should be for sun 1.5:
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

so I 

export JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

and also gedit /etc/environment to:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”
CLASSPATH=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11:.”

I reboot and still I get the same error. Where am I going wrong?

Thanks for the help in advance!
e123

---

### Post by jfinkels on 2007-07-31
> **e123 said:**
> Hi all,

Thank you all for your previous posts on pointing JAVA_HOME to the JDK. I worked through those I could find and no dice. I'll explain what I've done thus far and hope that someone can help me out. Thanks in advance!

My thinkpad T41 is running Ubuntu 7.04 with all the latest patches.

I downloaded the sun 1.5 JDK using the synaptic tool. I could not find any alternatives (besides 1.6). If there is an alternative that hides less well than the sun JDK I could really use it...

I also downloaded Netbeans 5.5 with synaptic.

When I attempt to compile my code in Netbeans this error message appears:
clean:
Deleting directory /home/mdj/apps/imagej/build
compile:
Created dir: /home/mdj/apps/imagej/build
Compiling 479 source files to /home/mdj/apps/imagej/build
/home/mdj/apps/imagej/build.xml:9: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK
BUILD FAILED (total time: 0 seconds)


It warned me that JAVA_HOME was not pointing anywhere. So I attempted to follow the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME](http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME)

As best I can tell this is what JAVA_HOME should be for sun 1.5:
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

so I 

export JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

and also gedit /etc/environment to:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”
CLASSPATH=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11:.”

I reboot and still I get the same error. Where am I going wrong?

Thanks for the help in advance!
e123

The directory you give here (/usr/lib/jvm/java-1.5.0-sun-1.5.0.11): are you certain that that is the correct java home directory?

---

### Post by thangdd on 2007-08-08
> **e123 said:**
> Hi all,

Thank you all for your previous posts on pointing JAVA_HOME to the JDK. I worked through those I could find and no dice. I'll explain what I've done thus far and hope that someone can help me out. Thanks in advance!

My thinkpad T41 is running Ubuntu 7.04 with all the latest patches.

I downloaded the sun 1.5 JDK using the synaptic tool. I could not find any alternatives (besides 1.6). If there is an alternative that hides less well than the sun JDK I could really use it...

I also downloaded Netbeans 5.5 with synaptic.

When I attempt to compile my code in Netbeans this error message appears:
clean:
Deleting directory /home/mdj/apps/imagej/build
compile:
Created dir: /home/mdj/apps/imagej/build
Compiling 479 source files to /home/mdj/apps/imagej/build
/home/mdj/apps/imagej/build.xml:9: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK
BUILD FAILED (total time: 0 seconds)


It warned me that JAVA_HOME was not pointing anywhere. So I attempted to follow the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME](http://ubuntuforums.org/showthread.php?t=217936&highlight=JAVA_HOME)

As best I can tell this is what JAVA_HOME should be for sun 1.5:
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

so I 

export JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”

and also gedit /etc/environment to:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
JAVA_HOME=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11”
CLASSPATH=“/usr/lib/jvm/java-1.5.0-sun-1.5.0.11:.”

I reboot and still I get the same error. Where am I going wrong?

Thanks for the help in advance!
e123

Hi!

I've same problem with you. But my problem because i've installed JRE but not JDK.
Please check, you maybe not install the JDK. If you install the JDK by Add/Remove... You have to check to select two component: JRE and JDK (sun java 5.0 console)

---

