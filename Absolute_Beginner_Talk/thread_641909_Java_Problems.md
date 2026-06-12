---
title: "Java Problems"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-16
Hi, I'm trying to run in-browser Java programs using FireFox (and I've tried using Epiphany), but I'm not having any success.
I have tried installing several different Java programs, such as Java Sun 7 and Sun Java 6 Web Start.

I hope someone can give me help. I have heard that a program called IcedTea makes Java programs work, I downloaded it, but I don't know how to install it.

Thanks in advance

---

### Post by rsambuca on 2007-12-16
How have you installed the plugin?

Are you using 32bit or 64bit Ubuntu?

---

### Post by Want A Pie on 2007-12-16
erm, the normal one I think...
and I don't know how I'm installing...

---

### Post by PmDematagoda on 2007-12-16
Post the outputs of:-
```

uname -a
```

And

```
sudo update-alternatives --config java
```

---

### Post by Want A Pie on 2007-12-16
dale@dale-laptop:~$ uname -a
Linux dale-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

dale@dale-laptop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by taurus on 2007-12-16
```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by Want A Pie on 2007-12-16
dale@dale-laptop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

still not working

---

### Post by taurus on 2007-12-16
You did restart firefox, right?  In the address field, type

```
about:plugins
```
and see if java 1.6 is on the list.

---

### Post by Want A Pie on 2007-12-16
Java 1.6 isn't on there
and yes, i restarted firefox

EDIT: Found this: application/x-java-bean;version=1.6 is that it?

---

