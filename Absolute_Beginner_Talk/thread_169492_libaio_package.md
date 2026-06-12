---
title: "libaio package"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by BrandNuUbantu on 2006-05-02
Hi there
I am trying to install oraclexe on my ubuntu. I am getting "libaio is not installed" .

Could some one please help me in fixing this.

TIA
BNU

---

### Post by testube_babies on 2006-05-02
Open up a terminal and type:
```
sudo apt-get install libaio
```

---

### Post by BrandNuUbantu on 2006-05-02
Dude
i did the same, i am getting this error " Libaio has no installation candidate". Dont know what that means?. But thanx for your time in replying.

BNU

---

### Post by halfvolle melk on 2006-05-02
edit:Here's an Ubuntu deb:
[http://rpm.rutgers.edu/repository/ubuntu/pool/main/liba/libaio/libaio1_0.3.104-1ubuntu6_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/main/liba/libaio/libaio1_0.3.104-1ubuntu6_i386.deb)

---

### Post by BrandNuUbantu on 2006-05-02
I did this after downloading ..
# dpkg -i libaio1_0.3.104-lubuntu6_i386.deb
This is the error i am getting. Any clues !
dpkg: error processing libaio1_0.3.104-lubuntu6_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libaio1_0.3.104-lubuntu6_i386.deb

TIA
BNU

---

### Post by halfvolle melk on 2006-05-03
> # dpkg -i libaio1_0.3.104-lubuntu6_i386.deb
This is the error i am getting. Any clues !
dpkg: error processing libaio1_0.3.104-lubuntu6_i386.deb (--install):
I think you misspelled the package name. Try this instead:
```
# dpkg -i libaio1_0.3.104-1ubuntu6_i386.deb
```

---

### Post by jvain2005@gmail.com on 2008-02-08
no need to take high road :-)

in ubunut libaio is called libaio1

so sudo apt-get install libaio1 should work. It worked for me. useful to install oracle-xe 

ubuntu-desktop:/opt/u01/downloads$ sudo apt-get install libaio1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libaio1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7750B of archives.
After unpacking 73.7kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libaio1 0.3.106-5ubuntu2 [7750B]
Fetched 7750B in 0s (19.0kB/s)
Selecting previously deselected package libaio1.
(Reading database ... 97149 files and directories currently installed.)
Unpacking libaio1 (from .../libaio1_0.3.106-5ubuntu2_i386.deb) ...
Setting up libaio1 (0.3.106-5ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

HTH

---

