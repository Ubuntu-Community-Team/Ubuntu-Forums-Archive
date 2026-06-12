---
title: "Yes/No Confirmation Before Installing in Ibook G4..."
date: 2010-07-26
forum: Apple Hardware Users
---

### Post by mcclinux on 2010-07-26
Hi Guys.

Just two quick questions. I know that a newbie question sometimes ticks people off but I'd really appreciate it if someone can confirm this for me.

I'd like to install Ubuntu on my iBook G4 [mid 2005 model].

I've spent hours reading this forum + ppcfaq and googling too, and I would appreciate it if someone can confirm these 2 for me:

1. I can run Java SE6
2. If I decide to go back to using Leopard 10.5.8, I can use the leopard install DVD to do it, by pressing "c" during bootup?

It's already half 2 in the morning my time, but from what I've read[my fatigue+sleepiness aside that is] I think these 2 things are possible.

Can anyone confirm please? :D

---

### Post by Macskeeball on 2010-07-26
#2 definitely is. That's completely independent of any installed OS.

---

### Post by mcclinux on 2010-07-27
thanks for replying!

the truth is ive toyed with linux for ages on my macbook, and I've always wanted to reformat my old iBook to a Ubuntu, but never did it as I've thought Leopard is really snappy on it.

Last night I tried running a Java app under 10.5.8 in iBook, and only then did I realized that Java SE 6 is incompatible with PPC Mac >> at least the Java that's applied from Apple is; and I don't know any way to force-install a Java 6 on 10.5.8 :sad: [sadder still is the fact that most probably this has been a very ancient issue, but I've only discovered about it now...]

Can anyone else confirm as per #1?

If not, I'll just close this thread then.....

---

### Post by zeroti on 2010-07-27
I have a 2004 Powerbook G4, and here are some results:

$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-4ubuntu3)
OpenJDK Zero VM (build 14.0-b16, interpreted mode)

$ apt-cache search sun-java6
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)

I was unable to install sun-java6-jdk -source or -jre. Either I don't have the right repositories installed, or it's not supported..?

It looks like at least with Debian, whose package manager Ubuntu uses, doesn't have a ppc version of sun-java6-jdk:

[http://packages.debian.org/lenny/sun-java6-jdk](http://packages.debian.org/lenny/sun-java6-jdk)

This might be helpful:

[http://blog.owensperformance.com/?s=Installing_Java_JDK_1_5_on_Ubuntu_Linux_PPC_6_06](http://blog.owensperformance.com/?s=Installing_Java_JDK_1_5_on_Ubuntu_Linux_PPC_6_06)

I'm curious to know what your decision will be.

---

### Post by zeroti on 2010-07-27
I just did a search for "jdk" using apt-cache and it showed "openjdk" i guess that can be an alternative:

$ apt-cache search openjdk
cacao-source - Source for CACAO, a Java virtual machine
default-jdk - Standard Java or Java compatible Development Kit
default-jdk-doc - Standard Java or Java compatible Development Kit (documentation)
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
freemind - Java Program for creating and viewing Mindmaps
icedtea-6-jre-cacao - Alternative JVM for OpenJDK, using Cacao
icedtea6-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
openjdk-6-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-6-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-6-doc - OpenJDK Development Kit (JDK) documentation
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot Zero
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot Zero (headless)
openjdk-6-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-6-source - OpenJDK Development Kit (JDK) source files
openjdk-6-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark
openoffice.org - office productivity suite


both the default-jdk and openjdk-6-jdk weren't complaining about not being able to install. I assume the jre's can install as well. ;-)

---

