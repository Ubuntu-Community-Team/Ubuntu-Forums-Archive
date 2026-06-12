---
title: "Java installation problems"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by scottym on 2006-10-08
I have successfull downloaded and installed the latest version of Java jre-1_5_0_09 but can not get it to be the recognized version of java. I have used the config-java command but do not get the option to select the 1.5 version of java. Also when I follow the instructions to install the bin package I get the following message:
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
replace jre-1_5_0_09-linux-i586.rpm? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: jre-1_5_0_09-linux-i586.rpm
error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_09-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_09-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_09-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_09-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_09-fcs.i586
        /bin/sh is needed by jre-1.5.0_09-fcs.i586

Basically I have tried everything i can find and am having no luck.Also  Synaptic lists the following for the program:
Java(TM) 2 Platform Standard Edition Runtime Environment
The Java 2 Platform Standard Edition Runtime Environment (JRE) contains
everything necessary to run applets and applications designed for the Java
platform. This includes the Java virtual machine, plus the Java platform
classes and supporting files.

The JRE is freely redistributable, per the terms of the included license.

(Converted from a rpm package by alien version 8.64.)

However, the program is not available in the alacarte menu.

---

### Post by ajgreeny on 2006-10-08
In a terminal type:-
sudo update-alternatives --list java
This should list the versions available on your machine and you can then pick the default you want.

---

### Post by scottym on 2006-10-08
It only lists 4.1 not the newer 5.0 version.

---

### Post by Max Luebbe on 2006-10-08
Did you download the ubuntu sun-java package?

That's an easy solution and what I use as a Java developer.

I know doing this will give you the option in update-alternatives.

```
sudo apt-cache search sun java
```

Should give you the package names, I can't remember what they are and am on a windows machine at work right now.

---

### Post by Max Luebbe on 2006-10-08
Oops, forgot to add that you will probably need the universe or multiverse repos to do this.

---

### Post by scottym on 2006-10-08
Hi Max
Synaptic is not letting me download the sun-java 5 package because it says it is no supportd. I unistalled the jre5 ver 9 and downloaded it as a .bin file executed it and it still is not recognized by the with the update-alternatives command.

I need this to run spamato in thunderbird. the jre1.5.0_09 folder is on the computer but i can't get synaptic or any thing else i have tried enable it.

It seems that gij-wrapper-4.1 tells ubuntu where the 4.1 files are but ihave ben unable to find gij-wrapper-5.0 if it exists to move it to the folder where wrapper is. I am nor to good at the seArches so it may exist but i can't find it.
thanks for the reply any other suggestions,

---

### Post by scottym on 2006-10-09
Finally figured out how to configure synaptic so it would download the sun-java files and got the new jre recognized but still have a problem. When i do java -version or any other commands i get the following message:

Error: Could not find libjava.so
Error: could not find Java 2 Runtime Enviromment.

Any suggestions about this problem?

---

### Post by Perfect Storm on 2006-10-09
Try this, it's allmost bullet proof: [http://ubuntuforums.org/showthread.php?t=267068&highlight=java](http://ubuntuforums.org/showthread.php?t=267068&highlight=java)

---

### Post by Ben Sprinkle on 2006-10-09
Just download the self extracting .bin from java.sun.com.

---

