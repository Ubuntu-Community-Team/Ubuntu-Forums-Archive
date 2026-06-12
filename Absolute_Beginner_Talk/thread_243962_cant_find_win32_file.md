---
title: "cant find win32 file"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-25
hey when i read about installing different codecs it says to put it in /usr/lib/win32 but in the lib folder there is no win32 folder. Where can i find it?

---

### Post by mssever on 2006-08-25
I don't know how to install them manually, but if you use [Automatix]("http://www.getautomatix.com/"), then it will install everything automatically.

---

### Post by aysiu on 2006-08-25
Where did you read that? Just paste these two commands into the terminal: ```
wget -c http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

---

