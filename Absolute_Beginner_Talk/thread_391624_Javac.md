---
title: "Javac"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-03-23
I really want javac to be able to compile code in java and not be in Eclipse. I would greatly appreciate if you could walk me through the steps to install the javac compiler on my computer.

Thank you.

---

### Post by dhtseany on 2007-03-23
> **jprb85 said:**
> I really want javac to be able to compile code in java and not be in Eclipse. I would greatly appreciate if you could walk me through the steps to install the javac compiler on my computer.

Thank you.


Do you have Java installed on your box? If I'm not mistaken, Javac will come with Java when you install it.

To see if you have java installed type:
```
$ java -version 
```

You should get an output that looks something like this:
[[IMG]http://img74.imageshack.us/img74/9081/screenshot2jp3.th.png[/IMG]](http://img74.imageshack.us/my.php?image=screenshot2jp3.png)

Reply back if you need help actually installing java.

---

### Post by upbeat.linux on 2007-03-23
You may need to add the appropriate repository, but this should do the trick:

> sudo apt-get install sun-java6-jdk

If you want, install the documentation:

> sudo apt-get install sun-java6-doc

---

### Post by jprb85 on 2007-03-24
Which repository do I need to add?

---

### Post by dhtseany on 2007-03-24
My personally written and detailed guide to setting up Java. If you have any questions ask...

To setup java:

Switch to root:
```
$ su root
```

Edit the following file:
```
$ gedit /etc/apt/sources.list
```

Add the following lines:
```

deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse

```

Save and exit. Then update the list:
```
$ sudo apt-get update
```

Install Java:
```
$ sudo apt-get install sun-java5-jdk
```

Finally, set new installation as default handler for Java:
```
$ sudo update-alternatives --config java
```



This is the terminal way of doing it. I believe you can also do it through either Synaptic or Applications -> Add/Remove...

And yes Gurus, I know I used sudo wrong but this way has worked everytime for me, so like they say "If it ain't broke then don't fix it" :)

Hope this helps..
Sean
```
</Bush>
```

---

