---
title: "Yahoo games and ubuntu unresolved problem, please help!"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by berlylabs on 2008-03-01
So I've become addicted to yahoo spades and I play it actively on my windows desktop while at school.  when I come home I bring my laptop that runs gutsy gibbon.  I have been trying to get yahoo games working on it for ages.  about:plugins shows i have a java plugin installed.  When i go to the site it tells me I don't have it installed or enabled and tells me to go to java site.  When i go there, if i click to test my java, it tells me its installed.  I also installed anything java via add/remove software.  Please help there has to be a way I'm desperate!:confused:](*,):cry::cry:

---

### Post by macogw on 2008-03-01
Which Java are you using?  What's the output of ```
update-alternatives --config java
```

---

### Post by berlylabs on 2008-03-02
There are 7 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/bin/cacao
          4    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        5    /usr/lib/j2se/1.4/bin/java
          6    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          7    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 


if i hit enter it just goes to a new prompt for a command

---

### Post by berlylabs on 2008-03-02
This is what I get for version

kimberly@Lappy:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
kimberly@Lappy:~$

---

