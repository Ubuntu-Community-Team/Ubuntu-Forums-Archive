---
title: "Speed problems"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by ruya on 2006-07-19
I noticed, when I was running a Java application, that it was much slower than in Windows. I have a Centrino with DOTHAN cpu, 1.6 GHz 2 Mb L2, 1024 MB RAM, running Ubuntu with Xgl. 
Does anyone know what the problem could be?

Thank you,
Rui

---

### Post by svaucher on 2006-07-19
There are many factors that would affect the performance of your app. You'll need to provide more info. 

Which jvm are you using? I use Sun or IBM's virual machine because they're still more complete than the one distributed with Ubuntu.

---

### Post by ruya on 2006-07-19
Hi,

Ok, sorry about that.

ruya@aquarium:~$  java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I am using Eclipse SDK
Version: 3.1.2
Build id: M20060118-1600 (Ubuntu version: 3.1.2-1ubuntu6)

Thank you
Rui

---

### Post by ruya on 2006-07-19
Sorry,

I was not using that jvm. Now I am and the speed is much better. :) Still, it is  a bit slower than windows. 
Is there a jvm even better than this or something else I can do? 
How can I see if the cpu is being correctly used (all things detected)?

Thank you,
Rui

---

