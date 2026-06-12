---
title: "Need help getting Java to install"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Kuron on 2007-04-10
Hello
Im having trouble getting these two packages to install through Synaptic Package installer
> 
sun-java6-bin
Sun Java(TM) Runtime Environment (JRE) 6

and
> 
sun-java6-jre
Sun Java(TM) Runtime Environment (JRE) 6

when i try and install them I get this error

> E: /var/cache/apt/archives/sun-java6-bin_6-00-0ubuntu1~dapper1_i386.deb: subprocess pre-installation script killed by signal (Segmentation fault)
E: /var/cache/apt/archives/sun-java6-jre_6-00-0ubuntu1~dapper1_all.deb: subprocess pre-installation script killed by signal (Segmentation fault)

If anyone could help me fix this problem it would be greatly appreciated

---

### Post by gordebak on 2007-04-11
Maybe first you should remove the packages with errors from /var/cache/apt/archives/ 
Then maybe you can install them from start.

---

