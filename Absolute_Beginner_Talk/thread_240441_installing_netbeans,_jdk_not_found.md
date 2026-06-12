---
title: "installing netbeans, jdk not found"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by ahh_Jebubs on 2006-08-20
Hey,

I'm a complete linux noob and just installed Ubuntu this morning (yesterday morning now I guess :rolleyes: ). I'm planning to use it just for java, and maybe dip into python. I've installed java through apt-get and think it all went in okay but the netbeans installer can't find the jdk.

Checking versions gives me:
```
don@desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
don@desktop:~$ javac -version
javac 1.5.0_06
javac: no source files
```
That bit above about no source files looks off but Synaptic tells me the following are all installed (version 1.5.0-06-1 for all):
sun-java5-bin
sun-java5-demo
sun-java5-doc
sun-java5-fonts
sun-java5-jdk
sun-java5-jre
sun-java5-plugin
sun-java5-source

I've spent hours reading various bits and pieces around the net and figure it's just the classpaths, so I have to sort out JDK_HOME and JAVA_HOME but I have no idea where apt-get installed the jdk to and Google has failed me on what to set the paths to.

I've spent all day trying to get this sorted (its now 2am), someone please put me out of my misery.

Cheers.

---

### Post by mlind on 2006-08-20
Try if **update-java-alternatives** solves this for you. You're currently using Gnu's java and should be using Sun's java instead.

---

### Post by ahh_Jebubs on 2006-08-21
Cheers mlind, that got it sorted :D 
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by robert114 on 2006-11-01
well thanx that worked for me on edgy as well!

I was just about installing java manually

---

