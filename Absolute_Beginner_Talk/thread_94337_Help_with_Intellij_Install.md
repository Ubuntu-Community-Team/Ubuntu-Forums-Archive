---
title: "Help with Intellij Install"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by michaelgatl on 2005-11-23
I'm kinda sorta new to Linux and I'm trying to install intellij and I'm having an issue with the install. The error is as follows:

ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
./idea.sh: line 61: /usr/lib/java: is a directory

I set the JDK_HOME and JAVA_HOME environment variables as follows:

1- set a symlink

ln -s /usr/lib/j2sdk1.5-sun /usr/lib/java

2- Set Environment Variable

export JAVA_HOME=/usr/lib/java
export JDK_HOME=/usr/lib/java

Any clue what I might be doing wrong?

Thanks,
Michael

---

### Post by jannol on 2006-02-15
maybe idea.sh cant follow symlinks, you could try

export JAVA_HOME=/usr/lib/j2sdk1.5-sun
export JDK_HOME=/usr/lib/j2sdk1.5-sun

---

