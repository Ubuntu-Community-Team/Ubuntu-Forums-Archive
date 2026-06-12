---
title: "Looking for easy ftp server"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-02-16
Looking for an easy to install and operate ftp server.

Its only ever going to have one account ,"Guest" , and a password

I'm not so hot on installing apps so ease of install is a key here. 

Any advice ?

---

### Post by frodon on 2007-02-16
Try this guide i wrote :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by koconnor100 on 2007-02-16
> **frodon said:**
> Try this guide i wrote :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

kevin@PROBLEMCHILD:~$ sudo apt-get install proftpd gproftpd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package proftpd
kevin@PROBLEMCHILD:~$

---

### Post by taurus on 2007-02-16
Looks to me like you need to enable both universe and multiverse in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
and remove the # from all the lines with deb in front.  Save it and run

```
sudo apt-get update
sudo apt-get install proftpd gproftpd
```

---

### Post by koconnor100 on 2007-02-16
"you must be in root to run gproftpd" 

What the heck ?

---

### Post by taurus on 2007-02-16
```
gksudo gproftpd
```

---

### Post by koconnor100 on 2007-02-16
> **taurus said:**
> ```
gksudo gproftpd
```

My goodness there's a working ftp server here.... think I'll throw that last command into a batch file if you don't mine ... :guitar:

---

### Post by taurus on 2007-02-16
Go for it.  ;)

---

