---
title: "Java JDK 1.5"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-10
Hi everybody

I need to install Java JDK 1.5 in order to install another programm (Webgoat), and I was wondering if there is a way to know if it already installed on my ubuntu 6.06.:confused: 
I don't kow anything about Java, if it comes as default or not.
I saw the Java site and I didn't event recognize the Java JDK 1.5 release.
:confused: :confused: 
So tahansk to anybody for any hint

---

### Post by biffta on 2006-11-10
Hi helphope,

the official java packages do not come pre-installed with Ubuntu. This is due to Sun's (current) licensing restrictions. What Ubuntu does with in terms of java is the jgc java compiler, but I suspect this is not going to help you and you goats. You will probably need to get the latest JDK (JDK 5.0 Update 9) from the [Sun site]("http://java.sun.com/javase/downloads/index.jsp")

---

### Post by Kieranties on 2006-11-10
you can check for java by typing in a terminal
```
java --version
```
If it does not have it then you will get some error such as 'unknown command'
I installed java using Automatix2, but I think it is in the repos, if it is then 
```
sudo aptitude install java
```
to get it.  Note you will have to agree to the eula that comes up in the terminal!

---

### Post by biffta on 2006-11-10
After looking a little bit more what this webgoat thing actually is it seems to me you need a full J2EE server to run it? This is not something you can really setup for yourself that easily.

---

### Post by helphope on 2006-11-10
Thanks to everybody fro replying


> **biffta said:**
> After looking a little bit more what this webgoat thing actually is it seems to me you need a full J2EE server to run it? This is not something you can really setup for yourself that easily.


Yes, I fear that ... it's a long way to Tipperary; but I don't want to give up so easily

Thanks

---

### Post by Gouki on 2008-02-10
> **helphope said:**
> Thanks to everybody fro replying





Yes, I fear that ... it's a long way to Tipperary; but I don't want to give up so easily

Thanks

All you need to install to run WebGoat:

```
sun-java5-bin sun-java5-jdk sun-java5-jre
```

---

