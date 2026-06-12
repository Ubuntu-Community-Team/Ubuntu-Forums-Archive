---
title: "at update unused packages will be removed"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-27
Hello all,

I am a bit stunned with the following statement as I did an update of my system with 
sudo aptitude update

**The following packages are unused and will be REMOVED:**
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl
  libplrpc-perl mysql-client-5.0 mysql-common mysql-server-5.0
The following packages have been automatically kept back:
  linux-image-server
The following packages will be upgraded:
  vim-common vim-tiny
2 packages upgraded, 0 newly installed, 8 to remove and 1 not upgraded.
Need to get 722kB of archives. After unpacking 90.5MB will be freed.
Do you want to continue? [Y/n/?] n

I installed mysql as a seperate packeage as I didn't install LAMP server in edgy server 6.10
My question ? Why is the system assuming that the mysql package is not in use, even when the server is started up. Am I not able to install mysql without LAMP server ?
As I don't want to remove it, I am also not able to upgrade the packages mentioned as well as it is packed in one question.

How do I have to deal with this as I
1. want to keep mysql, and
2. would like to upgrade the other 2 packages. 

Any explanation from the Linux Pros to an Linux Newbie would be welcome.

---

### Post by 5-HT on 2007-04-28
> Why is the system assuming that the mysql package is not in use, even when the server is started up. Aptitude marks packages and their dependencies as being either automatically installed or manually installed. Any packages with the 'automatically installed' flag that are not claimed as dependencies by any currently installed packages are selected for removal.
When aptitude is saying those packages it wants to remove are not in use it does not refer to programs actually being run at the moment, but rather that no other package is claiming dependencies on them and that they are marked with the auto flag.


```
Am I not able to install mysql without LAMP server ? 
```You most certainly are.
```

As I don't want to remove it, I am also not able to upgrade the packages mentioned as well as it is packed in one question.

How do I have to deal with this as I
1. want to keep mysql, and
2. would like to upgrade the other 2 packages. 
```**Ia) **Is mysql-server-5.0 marked as automatically installed? By setting unmarking the auto flag, aptitude should stop trying to remove mysql-server-5.0 and its dependencies.

To check the flag:
```
aptitude show mysql-server-5.0
```To mark as manually installed:
```
sudo aptitude unmarkauto mysql-server-5.0
```** Ib) **If mysql-server-5.0 is already marked as manually installed, you can  try to reinstall it using aptitude (just to reselect it, it will not actually reinstall the whole program). Also, you could install mysql-server (a metapackage that depends on mysql-server-5.0 at this point in time).

** 2)** Once aptitude is no longer trying to remove mysql you can grab the updates with aptitude, or just install the updates with apt-get.

Hope that helps

---

### Post by ottawa on 2007-04-29
Thank you 5-HT for the clear and good explained information.


ottawa

---

