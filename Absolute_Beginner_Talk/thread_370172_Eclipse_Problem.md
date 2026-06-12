---
title: "Eclipse Problem"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-25
I recently installed Eclipse from application and add/remove programs. Although I installed it, it gives me this message:


A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

I would greatly appreciate if you could walk me through the steps about how to fix this problem so that I can start using Eclipse.

Thanks

:popcorn:

---

### Post by n8bounds on 2007-02-25
add all repose and in a terminal say:
```

sudo apt-get update && sudo aptitude search sun

```
The results from that search should be enough to get you started.  If you dont see one that says sun java jdk or something like that, you have your repos (sources.list) screwed up

---

### Post by jprb85 on 2007-02-25
Thanks

---

### Post by phossal on 2007-02-26
The packaged version of Java's JDK 6 you can get like this:
```
sudo apt-get install sun-java6-jdk
```

It's a backports project though, so I'm not in love with that. You'll have to enable the backports repositories to get it. I usually install my primary Java using the .bin file SUN makes available on their website at [http://java.sun.com](http://java.sun.com). The backports package is prepared using that anyway. Once you've installed a JDK, using either method, make sure to enable it by running:
```
sudo update-alternatives --config java
``` and selecting the appropriate one.

---

