---
title: "Java Problems?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2007-08-14
I have java 6 installed but I think I'm having some problems:
First Netbeans will not load or let me go past the licensing agreement (no words show up)
Second when using Eclipse (since I couldn't get Netbeans to work) it does not find any of the classes such as the Scanner class.
Thirdly programs such as Nexuiz that run java crash while running.

Does anyone have any answers to these problems?

---

### Post by Bagster on 2007-08-14
These could all have a variety of solutions.....


The most obvios is that although sun java6 has been installed, it is not being used for running these programs. To check this run
```
sudo update-alternatives --config java
```

and make sure that you are actually using sun java 6. The gcj version has quite a few problems, such as causing azureus to crash - it is possible that it could also cause other things to fail.

as for the eclipse problem, open eclipse go to 

window>preferences>java>compiler and change the Compiler compliance version to 6.0 - the latest version. You will also have to make sure that eclipse is using the correct JRE under the java>installed JREs tab

---

### Post by Holmes89 on 2007-08-14
Which is the most current JRE? and if mine is old how do I add a new one?

---

### Post by Holmes89 on 2007-08-14
Nexuiz still crashes and Netbeans still doesn't work

---

### Post by Bagster on 2007-08-14
the jre is the java runtime environment. It is the part of java that actually runs the code. If you have installed sun java 6 you will have the java6 runtime environment.

Incedentally, if you want to program using java 6 you also have to install the java development kit - this allows you to compile the code using java6. to make sure you have this:

```
sudo apt-get install sun-java6-jdk
```

---

### Post by Bagster on 2007-08-14
hmm and you definitely have the correct java selected -   /usr/lib/jvm/java-6-sun/jre/bin/java
in the update alternatives?

dont really know of any other obvious solutions then - I assume you have tried reinstalling netbeans? 

Did the eclipse thing work? Are you now seeing all the classes?

---

### Post by Holmes89 on 2007-08-14
I got the JRE fixed, thanks. I just had to do a search in the /usr/lib/jvm/java-6-sun/ and I found it so now my classes work, but my netbeans still doesn't work, is it any good anyway? Also Nexuiz doesn't work, I don't know if that has a different problem.

---

### Post by Bagster on 2007-08-14
I've never used Nexuiz, so cant really help there. I prefer netbeans to eclipses, with the new beta for netbeans 6 being in my opinion much better then the current version of eclipse - In fact I'm using it at this moment.... 

However it is personal taste, and a lot of people will totally disagree with what I  think.
If you really want to get it working you could try not use the repository version and install it manually, by downloading the .bin from [http://www.netbeans.org](http://www.netbeans.org) As I said I think the 6.0 beta is definitely worth a look, and you cant get it through the repositories

---

