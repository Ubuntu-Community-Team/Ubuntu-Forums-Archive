---
title: "Java spiking CPU"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-09
is there any known issue with the JRM 1.5 becuase while using Eclipse sometime the java process spikes to 50-60 percent and Eclipse becomes unresponsive.

---

### Post by ctyc on 2008-03-10
the known issue is java is slow and crappy.

---

### Post by themusicwave on 2008-03-10
Don't listen to the Java sucks stuff you constantly hear.

Java is slower than C, but it isn't that much slower.  Most people who complain about Java speed either haven't used Java since it first came out(when it was slow) or are using the Crappy GNU version of Java.

You need the real Sun JRE.  it can be installed from the repositories.

The packages you want are:
sun-java6-jdk
sun-java6-jre

These will run much faster than the GNU equivalent.  Also, Sun's Java is now open source, so if thats a huge deal to you then don't worry about it.

Run:
java - version 

It will tell you what version of Javayou have installed.  Mine says:

java version "1.6.0_03"

Also, how much RAM do you have?  Eclipse needs a good bit of it.  In fact what are your specs in general?

You could also give netbeans a try, I like it better than eclipse, but it is a matter of preference.

---

### Post by RyanZec on 2008-03-11
i have version 1.5..0_13

I have to say that the programs that i have used the run on java(like eclipse and zend studio) have been buggy and slow(but eclipse is much faster on ubuntu than XP).  Also I am using eclipse for PHP and C++ development stince it has the best feature set of any IDE for those programming languages.

---

