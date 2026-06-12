---
title: "upgrade to edgy"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-12-23
I've been grounded for a while and now I've got my computer back.  I forgot how to do everything on Linux!  Could someone help me upgrade to Edgy?

---

### Post by taurus on 2006-12-23
Are you running Dapper right now?  Here's a guide to upgrade from Dapper to Edgy...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Drakkor on 2006-12-24
If you can just clean install Edgy

---

### Post by elcasey on 2006-12-24
I'm trying to upgrade myself and am having a problem.

I run [FONT="Courier New"]gksudo "update-manager -c"[/FONT], click "Upgrade" and it downloads some files. As soon as it goes to "Modifying Software Channels" I get the following error message(s):
```
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz 404 Not Found
```

I edited my *sources.list* file to read "edgy" instead of "dapper" and it still gives me an error. What's going wrong and how can I fix it? :-k 

Thanks in advance!

---

### Post by taurus on 2006-12-24
It's always a good idea to comment out those extra repos in /etc/apt/sources.list when you upgrade from one release to the next!  Therefore, put a # in front of these lines in /etc/apt/sources.list...

```
#http://packages.freecontrib.org/ubuntu/
```

---

### Post by elcasey on 2006-12-24
That did the trick. Thanks very much! :)

---

### Post by newpants2003 on 2006-12-25
good!!

---

