---
title: "help installing java 1.5"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by csavio on 2007-03-26
I am having trouble installing java version 1.5 on Ubuntu (6.10).  I followed the directions at:  [http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part](http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part)  to a tee and everything went fine.
However, the directions tell me that when I do a "java -version", this message should appear: 
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

But it doesn't!!! Instead, I get: 
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

I do have the directory /usr/lib/j2sdk1.5-sun and this is where it was installed to.  Please help! I'm going nuts! This is so frustrating!

~Caroline

---

### Post by digital_sabotage on 2007-03-26
search for "sun-java5-jre" or just "jre" in >System>Adminstration>Synaptics package manager ...that's where i installed it from ...gave me version 1.5 ...either way it should tell you what version you do have ...good luck:-)

---

### Post by csavio on 2007-03-26
Thanks for the reply.  I went into Synaptic and it shows me that it's already installed.  I went back into the terminal and did a "java -version" but it's still telling me that I have the blackdown standard edition... :(

---

### Post by csavio on 2007-03-26
Nevermind, I did a "update-alternatives --config java" and selevted 1.5 as the default :KS

---

### Post by zvacet on 2007-03-27
So now you can go for 1.6

---

