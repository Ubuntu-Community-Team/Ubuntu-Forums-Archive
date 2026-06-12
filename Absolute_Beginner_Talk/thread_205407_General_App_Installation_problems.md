---
title: "General App Installation problems"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Cesium on 2006-06-28
Hi,

I am having problems installing any applications.  I just installed Dapper, used automatix to get some apps, and then installed amarok.  Now I can't install programs like firestarter.  Here is what I get:


post@Boogieman:~$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter


Thanks for any help!

---

### Post by Dr. Nick on 2006-06-28
your sources.list file may be messed up.

Run from a terminal

**sudo apt-get update**

and see if you get any error messages and yo may also look at the file /etc/apt/sources.list and make sure it all looks right. If you dont see a problem you can post the file here  and see if someone else sees one, or just make a new one using this

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

I havent used automatix lately, but If I recall it adds a few things to the sources.list which may be giving you errors

---

### Post by Cesium on 2006-06-28
Thanks Dr. Nick!

When I do sudo gedit /etc/apt/sources.list  my sources.list comes up empty/blank.  Doing sudo apt-get update just gives me:

post@Boogieman:~$ sudo apt-get update
Reading package lists... Done
post@Boogieman:~$ sudo gedit /etc/apt/sources.list


I assume that is why I am getting these errors.  What should I put in for the sources.list then?  Thanks again and nice Simpsons avatar.

---

### Post by aysiu on 2006-06-28
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) will help you get a working sources.list

---

### Post by Cesium on 2006-06-28
Thanks. That did the trick.

---

### Post by arnieboy on 2006-06-28
[QUOTE=Cesium]Hi,

I am having problems installing any applications.  I just installed Dapper, used automatix to get some apps, and then installed amarok.  Now I can't install programs like firestarter.  Here is what I get:


post@Boogieman:~$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter


Thanks for any help![/QUOTE]
which version of ubuntu dapper are u using? 386/amd64/ppc ?

---

