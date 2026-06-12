---
title: "installing programs"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by addman on 2007-05-07
its my first time using a linux system without linspire's CNR system and i cant install anything
so i was wondering if someone could teach me how to intall limewire with some very basic step by step instructions. the ubuntu installer had an error that said ERROR: Dependency is not satisfiable: sun-java5-jre  sun-java6-jre  sun-java5-jdk  sun-java6-jdk



thanks for any help

---

### Post by noob12345 on 2007-05-07
System-> Adminstration-> Synaptic
when its open, go to Settings-> Repository. make sure all of them are checked
press search, then find all the packages you need, marking them for installation. click apply
that should solve your dependency issues

---

### Post by overdrank on 2007-05-07
> **addman said:**
> its my first time using a linux system without linspire's CNR system and i cant install anything
so i was wondering if someone could teach me how to intall limewire with some very basic step by step instructions. the ubuntu installer had an error that said ERROR: Dependency is not satisfiable: sun-java5-jre  sun-java6-jre  sun-java5-jdk  sun-java6-jdk



thanks for any help

Hi you could use automatix and it will install the java and frostwire for you. Good luck!

---

### Post by NeoLithium on 2007-05-07
A great way for some rather common installations is [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  They have step by step walkthroughs that should get you up and running for everything.  I recommend learning this way far more than automatix.

---

### Post by aysiu on 2007-05-07
Dependency errors usually stem from conflicting repositories.

[Get a fresh set](http://www.psychocats.net/ubuntu/sources) and try again.

You don't need CNR--use Synaptic (don't forget to click **Reload**):
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by addman on 2007-05-07
ok now theres another problem =(



ERROR: Dependency is not satisfiable: libc6

---

### Post by Sef on 2007-05-07
1) Have you installed Feisty Fawn, 7.04?

2) > you could use automatix

With Feisty Fawn, automatix is no longer really needed.  Also automatix is known for creating problems for some users.

---

### Post by NeoLithium on 2007-05-07
sudo aptitude install libc6

Make sure you are using a fresh source list as provided by aysiu; and you shouldn't have any problems.

---

### Post by addman on 2007-05-07
>_< ok ill look it up if it didnt come with version 6.06.1 of ubunto i prolly dont have it

---

### Post by NeoLithium on 2007-05-07
Ok, if you're running Ubuntu 6.06, you can take a look right here:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

That is a walkthrough to add the proper repositories for you, and you should be able to install java, etc, without any problems. :)

Hope this helps :)

---

### Post by addman on 2007-05-07
im completely lost what do i do with repositories???

---

