---
title: "Gcc"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by xander223 on 2007-09-20
Okay, this is my first attempt at a true Linux system in any great length. I took an abbreviated (very) course on Unix / Linux code back like 3 years ago and hardly remember anything. I have code that I wish to compile already written. The problem is the C Compiler needs GCC for something. Well, I found GCC 4.2.1 and downloaded it. I don´t know if what I got is right or not. The C Compiler I got is the Non-Commercial Intel 10. Is there anything I should be aware of by way of installing these things. Changing from XP to Linux has been a very mind boggling experience thus far with no friends to guide me along the way like I´ve had in the past (in person that is because I´ve found forums for Linux not only very helpful but quite kind to newbies like me). Any help at this point would be much appreciated. Directions to reading material or reference material would also be welcome.

---

### Post by rsambuca on 2007-09-20
That is actually a newer version of the Gnu C Compiler than the one in the repositories.  Although I know nothing of programming, just as a reference for the future, you may want to check the Synaptic Package Manager first to see if it has the packages you require.  If you go to the top menu bar you will find it under "System -> Administration".  Synaptic is kind of one-stop shopping for all of the Ubuntu packages, so you just select the desired package for installation and click apply.

---

### Post by RomeReactor on 2007-09-20
Hi. I don't know much about compiling, but you should install **build-essential**; it will provide you with the necessary tools: Look for it in Synaptic (SyStem->Administration->Synaptic Package Manager). Or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install build-essential
```

---

### Post by RedSquirrel on 2007-09-20
For many programming tasks, you will want to simply install the **build-essential** package from the repositories.

Be sure to check out the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum, which has several sticky threads that might help you out.

---

