---
title: "RPM package installation fails because it needs /bin/sh ... which i have! what's up?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-13
hey there. 

i'm trying to install a program that's distributed via .RPM format. of course, it's failing right from the start. weirdly enough, it says it's missing a dependency; SH. of course i already have SH installed. wtf? here's the error code : 

> root@jason-laptop:/mnt/dvdrom/Maya/linux# rpm -ivh AWCommon-10.80-13.i686.rpm
error: Failed dependencies:
        /bin/sh is needed by AWCommon-10.80-13.i686
root@jason-laptop:/mnt/dvdrom/Maya/linux#

and just to prove that SH does indeed exist, here's this bit too :

> root@jason-laptop:/bin# ls sh*
sh  sh.distrib
root@jason-laptop:/bin#

any idea what's going on?

---

### Post by rickycodie on 2007-09-13
there is a package available in the repo's called alien, it turns rpm and others into deb's. try that. also here are some  instructions

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Lacrimstein on 2007-09-13
The installation package you are trying to install requires to be run in the sh shell. By default, Linux uses the bash shell. Try this:

sh
sudo rpm -ivh AWCommon-10.80-13.i686.rpm

---

### Post by ijason on 2007-09-13
**@rickie**. are RPM not natively supported by ubuntu?

---

### Post by ijason on 2007-09-13
**@Lacrimstein**, thanks for the suggestion. but it didn't work :(

> root@jason-laptop:/mnt/dvdrom/Maya/linux# sh
# rpm -ivh AWCommon-10.80-13.i686.rpm
error: Failed dependencies:
        /bin/sh is needed by AWCommon-10.80-13.i686
# 
# 

for good measure i tried SHing in different order, but it didn't work either.

> root@jason-laptop:/mnt/dvdrom/Maya/linux# sh rpm -ivh AWCommon-10.80-13.i686.rpmsh: Can't open rpm

---

### Post by Lacrimstein on 2007-09-13
thats strange check if rpm is on your system. it is on mine, and i don't recall intentionally installing it... check the repos

---

### Post by Lacrimstein on 2007-09-13
oh :)
you put it all on the same line
first type in sh, then hit enter
then enter the rpm command

---

### Post by ijason on 2007-09-13
**@Lacrimstein**. yep, the first time i tried it that's what i did... the # prompts are the SH ... uh ... interface. 

i'll try once more to make certain that i did it in seperate lines :)

> root@jason-laptop:/mnt/dvdrom/Maya/linux# sh
#          
# rpm -ivh AWCommon-10.80-13.i686.rpm
error: Failed dependencies:
        /bin/sh is needed by AWCommon-10.80-13.i686
# 
# 

---

### Post by Lacrimstein on 2007-09-13
oh! try this:

sudo alien <packagename.rpm>

this will convert the rpm to a deb.
if alien isn't recognized, try

sudo apt-get install alien

---

