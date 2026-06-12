---
title: "Help WIth Installing Programs!"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by jckbac9 on 2006-07-26
Hey, i am fairly new to linux and i am using Kubuntu. I love it, but i am considering to move back to suse. i cant install almost any programs, in kubuntu! most .deb packages dont work, errors often accour. more importantly whenever i try to install a program, for example alien (to convert .rpms to .deb files), the following happened. 

$sudo apt-get install alien
Reading Package lists... Done
Building dependency tree... Done
E.Couldn't find package alien

for anything i try to install it says at the end, E.Couldn't find package ...
can somebody please help a (k)ubuntu newbie?!!

---

### Post by jordilin on 2006-07-26
alien is in the repos. You should have universe and multiverse, sth like
> deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

then do:
```
apt-get update
```

then go to synaptic and try again :D

---

### Post by deadgobby on 2006-07-26
> **jckbac9 said:**
> Hey, i am fairly new to linux and i am using Kubuntu. I love it, but i am considering to move back to suse. i cant install almost any programs, in kubuntu! most .deb packages dont work, errors often accour. more importantly whenever i try to install a program, for example alien (to convert .rpms to .deb files), the following happened. 

$sudo apt-get install alien
Reading Package lists... Done
Building dependency tree... Done
E.Couldn't find package alien

for anything i try to install it says at the end, E.Couldn't find package ...
can somebody please help a (k)ubuntu newbie?!!

[http://ubuntuguide.org/wiki/Dapper#limewire](http://ubuntuguide.org/wiki/Dapper#limewire)
Please look at sections 18:23 and 18:24. 
The computer is thinking you are trying to install just a package name alien. It does not know where to find package alien. 
So if you DL a deb package and lets save you save the DL pack to the desk top. At the Terminal.
$ cd Desktop
$ ls ( LS in lower caps this will list docs on the desktop and look for the deb pack name)
$ sudo apt-get dpkg -i debianpackagename.deb
 If you have a RPM. This is where the alien command comes in. So
$ sudo alien packangename.rpm

Good luck
GObby

---

### Post by jckbac9 on 2006-07-27
hey thanx for the help deadgobby, BUT, it didnt work. i tried your instructions out for a repository of realplayer 10. after i typed in cd desktop it said no such file or directory. so i just skipped that instruction. after that i typed in the Is, and it had an error. after that i typed in sudo apt-get dpkg -i realplayer_10.0.7-0.0_i386.deb, and it said E: Command line option 'i' [from -i] is not known. So, after all of this i tried it without the -i, and it said invalid operation dpkg.
Can you (or someone else) please HELP!!!!!  and thanks for the help jordilin, but when i tried to install alien it didn't work.

PLEASE HELP!!!!!!!!!!!!

---

### Post by Drakkor on 2006-07-27
I have just downloaded the .deb files to the desktop,double-clicked on them,and they installed fine ! ;)
[http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)

---

### Post by aysiu on 2006-07-27
While it's a good idea to have extra repositories enabled, you don't need them for *alien*.

It sounds as if you don't have *any* repositories enabled if you can't get *alien*.

Do this:

1. Follow [these instructions to get a good sources.list](http://www.psychocats.net/ubuntu/sources). Make sure you paste **over** your old sources.list.

2. Paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install alien realplayer
```

---

