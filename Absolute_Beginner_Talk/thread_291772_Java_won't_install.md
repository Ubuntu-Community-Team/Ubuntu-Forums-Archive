---
title: "Java won't install"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by grimsanta on 2006-11-02
Ugh, sorry for all the questions, brand new to this stuff.  It seems that if it's not one thing, it's another.

So I downloaded frostwire, and it won't start or do anything, so I assume that it's because I don't have Java Installed, correct?

I'm trying to install it, so i downloaded the package, installed it, downloaded the runtime environment, and i'm stuck here.  I do "fakeroot make-jpkg jdk-1_5_0_09-linux-i586.bin" and it tries loading all sorts of java related plugins, but then says no matching plugins were found, what do I do here?

---

### Post by Paul41 on 2006-11-02
I don't know about frostwire, but if you want a jre it is available in the repositories. For you Sun version.
> sudo apt-get install sun-java5-jre
You have to have multiverse enabled in your sources to get this one.

---

