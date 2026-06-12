---
title: "Installing LAMP on Desktop."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-20
I recently had a nightmare mishap when following this guides Feisty paragraph
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> **To install the default LAMP stack in Ubuntu 7.04 (Feisty Fawn)**
In Feisty, the Ubuntu base system includes Tasksel. You can install LAMP using tasksel.
```
sudo tasksel
```
And pick the LAMP option. 
Long story short I did it in a way so that it erased my entire Desktop environment including all 3'rd party programs.  But I'm OK I just needed to re-install /root partition again.
Which brings me back to square one before this happened.  In Dapper I installed LAMP on my Desktop with this commandline.
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
```
Can I still use the same line to install LAMP on my Feisty Desktop?

---

### Post by Mornedhel on 2007-07-20
Yup.

If you did it on Dapper, it's the exact same procedure on Feisty. (Works for me.)

---

### Post by jingo811 on 2007-07-20
Tnx for the confirmation.

---

### Post by Copter on 2007-07-23
A nice alternative to install whole LAMP package
[http://ubuntuforums.org/showpost.php?p=2950847&postcount=11]("http://ubuntuforums.org/showpost.php?p=2950847&postcount=11")

copter :]

---

### Post by jingo811 on 2007-07-24
Holy crap that's some ultra fast install procedure.  Why didn't they write that in Ubuntu Documentations Guides in the first place so I didn't have to go through hell a few months ago.

---

