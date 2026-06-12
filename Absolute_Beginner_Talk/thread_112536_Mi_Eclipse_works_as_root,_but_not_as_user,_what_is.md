---
title: "Mi Eclipse works as root, but not as user, what is wrong?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by zenitem on 2006-01-04
I've installed eclipse and I have the sun jdk 1.5, wen I run eclipse as root it works perfectly, but when I'm as user it doesn't, can anybody help me please??

:confused: 

this is my output when I use update-alternatives as user:

[B]enrique@PCDepa:~$ sudo update-alternatives --config java
Password:

There are 2 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-wrapper-4.0
*+ 2 /usr/lib/jvm/java-gcj/bin/java[/B]

I think that there should be the path to the jvm of sun, but when I exectute eclipse as root it appears:

[B]root@PCDepa:/home/enrique# eclipse
using specified vm: /usr/local/jdk1.5.0_06
[/B]

I't is confusing for me.

---

### Post by TrevorNet on 2006-03-09
Ditto on the running eclipse as root and not a normal user. At least at work. At home, I have no problem. Eclipse fires up and runs as expected without having to resort to sudo eclipse. Crazy, strange, weird... anyone?

---

### Post by mlind on 2006-03-09
you may haveto tell alternatives that sun's JVM is installed.
use *update-alternatives* script. add new jvm to /etc/jvm file too.

```

sudo update-alternatives --install /usr/bin/javac javac /usr/lib/j2sdk1.5-sun/bin/javac 120
sudo update-alternatives --install /usr/bin/java Java /usr/lib/j2sdk1.5-sun/bin/java 120

```

It's suggested to also set JAVA_HOME environment variable for java programs
you're running. you can define this on ~/.bashrc file.

---

### Post by mlind on 2006-03-09
btw. why do you run eclipse as root? :confused:

---

### Post by Dakmor on 2006-12-29
I had this kind of a problem.
Solution was to delete **.eclipse** directory in my home-folder. After it eclipse was loading  normally.

---

