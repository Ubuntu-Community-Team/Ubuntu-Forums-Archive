---
title: "I Botched My Java, How To Reinstall?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-04-16
Hi guys,

I was trying to Install Java SDK last night(for netbeans and eclipse), and after following various guides, I think I botched my java, now I can't even start azureus :(

I think what botched it was:
```

sudo update-alternatives --remove-all java
sudo update-alternatives --display java
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 601
sudo update-alternatives --display java

```

:(

```

kinson@ubuntu:~$ sudo update-alternatives --config java
Password:

There is only 1 program which provides java
(/usr/lib/j2se/1.4/bin/java). Nothing to configure.
kinson@ubuntu:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/Java6u1/bin/java
/usr/lib/j2se/1.4/bin/java - priority 1411
 slave java.1.gz: /usr/share/man/man1/java.j2se14.1.gz
 slave java.ja.1.gz: /usr/share/man/ja/man1/java.j2se14.1.gz
Current `best' version is /usr/lib/j2se/1.4/bin/java.
kinson@ubuntu:~$

```

I've tried installing the JRE/JDK (java5 and java6) from the command line, but nothing seems to be added, I also tried installing using Automatix, but it still didn't help me get azureus working again :(

Any help out there how to restore my Java? 

Thanks guys :)
Kinson

---

### Post by NeoLithium on 2007-04-16
If I remember right; the java to install for Azureus and a great deal of programs is 
```

sudo aptitude install sun-java6-jre sun-java6-plugin

```

For a simple way that always got my eclipse up and running; check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by kinson on 2007-04-16
I tried that, but I think it isn't updating anything :(

```

kinson@ubuntu:~$ sudo aptitude install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  sun-java6-plugin
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1364B of archives. After unpacking 65.5kB will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper-backports/multiverse sun-java6-plugin 6-00-0ubuntu1~dapper1 [1364B]
Fetched 1364B in 4s (339B/s)
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 119275 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-0ubuntu1~dapper1_i386.deb) ...
Setting up sun-java6-plugin (6-00-0ubuntu1~dapper1) ...

kinson@ubuntu:~$

```

I think I tried the steps in the Ubuntu guide before(after I botched this), and it didn't help :(

I'm using Dapper btw :/

Thanks,
Kinson

---

