---
title: "eclipse/java problems"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Gweilo on 2006-05-27
Hi,
I somehow can't get eclipse running correctly on my Ubuntu Dapper. 

When I press "Run >> Run..." nothing happens. normally a selection window should appear where I can set the parameters (for example) for the java program to run.
This window would be called "create, manage, and run configurations"

right clicking Main.java and selecting "Run as >> Java Application" works though

Does anybody know what could be wrong?

******************************************
my settings:
java RE in the build path shouldn't be the problem (is set to /etc/lib/j2re1.5-sun or */j2sdk1.5-sun)

My guess would be that eclipse uses the wrong java VM? Or possibly I have to use another version of eclipse for sun-java-1.5?

```
[13:40:45] ~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      4        /usr/lib/j2re1.5-sun/bin/java
*     5        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 5
Using `/usr/lib/j2sdk1.5-sun/bin/java' to provide `java'.
```

in /etc/jvm I have
```
/usr/lib/j2sdk1.5-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr
```

Thanks!

---

### Post by Gweilo on 2006-05-29
Downloading a fresh copy from eclipse.org and removing the versions from apt did the trick. now it works like a charm :)

---

