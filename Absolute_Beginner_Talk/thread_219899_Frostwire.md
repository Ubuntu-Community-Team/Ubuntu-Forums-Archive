---
title: "Frostwire"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-07-20
I just reinstalled Ubuntu Dapper, and I installed Forstwire and JRE from automatix. When i go to run frostwire in terminal i get this
```
Java exec not found in PATH, starting auto-search...
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

any suggestions?

---

### Post by mattisking on 2006-07-20
Did you install sun-java5-jre (multiverse) package? Once you've installed java (particularly if you have multiple packages installed) you need to tell the OS what version is the default. You can do this by running:
sudo update-alternatives --config java

tell it which to use.

---

