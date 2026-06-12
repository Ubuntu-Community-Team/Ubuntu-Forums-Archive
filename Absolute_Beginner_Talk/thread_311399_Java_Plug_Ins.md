---
title: "Java Plug Ins"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by MOTOboat on 2006-12-02
I have Dapper Drake (6.06) on a LAPTOP and am using Firefox 1.5.08.

I want to play Runesap but it ays I need to download the Java plug in.

I have Java enabled in preferences and Synaptic Package mnager does not provie any other Java type packages. Java Run time enviornment.

I thought I should use Package manager for all my istallations. Do I need to:

1) Up date to FF 2.0?
2) add in Java Plugins Manaually ([http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp))

If I do this manualy, will this cause problems?

Any direction is apreciated. Brand new Linux user

MOTOboat

---

### Post by TerryHowe on 2006-12-02
The manual install would be fine.  It isn't going to show up in Synaptic because Java is under a different license.  Alternatively, you can install something like automatix and run that to install Java.

---

### Post by Sef on 2006-12-02
> 2) add in Java Plugins Manaually ([http://java.com/en/download/manual.jsp)](http://java.com/en/download/manual.jsp))

Java is available through the multiverse repository. 

How to [add repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

> The manual install would be fine. It isn't going to show up in Synaptic because Java is under a different license.

Now it is in the multiverse repository because of license changes.  It has been for a few months.   Once it is open sourced, it will be available in universe.

> Alternatively, you can install something like automatix and run that to install Java.

The preferred way would be through multiverse.   Automatix can work well, but it can mess up your system too.

---

### Post by tarasbulba on 2006-12-02
There is no problem in manually install.i'm using edgy but this will work on dapper too,i suppose.Just download jre 1.5 update 09 from java site.Make multiverse repository enable.apt-get install "java package" package.cd to jre directory in terminal and type make-jpkg <filename>.it will create an installable .deb package.install it.

---

