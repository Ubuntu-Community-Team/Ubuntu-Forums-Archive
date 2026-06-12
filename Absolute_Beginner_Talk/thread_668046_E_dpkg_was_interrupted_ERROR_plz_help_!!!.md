---
title: "E: dpkg was interrupted ERROR plz help !!!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by tr4shp33l on 2008-01-15
i try installing limewire for Linux ubuntu, and its stop and freeze, so i restart and now cant acces to my 
synaptic packet... it say...Error...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

so i open the terminal and i write :  dpkg --configure -a
but it tell me now i have to be superuser to do this, seem like i dont have VIPacces on my own PC !?!

so maybe somebody want to wrote me line by line in order what i shoul do to fix this !

Thanks you

---

### Post by Rocket2DMn on 2008-01-15
Hehe, you need to use [sudo]("https://help.ubuntu.com/community/RootSudo").
```
sudo dpkg --configure -a
```
Enjoy :)

---

### Post by PeterJS on 2008-01-15
Try
```

sudo dpkg --configure -a

```
Linux has an actual security and permissions system in place, so even when running as an admin account you only have admin privliages when you explicitly request them with sudo or gksudo.

---

### Post by tr4shp33l on 2008-01-15
AHHH Thanks a lot guys !

BTW what is the difference between sudo and gksudo?

---

### Post by PeterJS on 2008-01-15
Sudo is command line, gksudo is graphical.

---

### Post by Rocket2DMn on 2008-01-15
gksudo is used for running GUI applications with root privileges.  There is a security reason why they had to create gksudo - see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

