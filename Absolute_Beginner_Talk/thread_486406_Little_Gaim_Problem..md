---
title: "Little Gaim Problem."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-28
Ok, i have msn, aim, and yahoo on gaim. It always was fine until earlier I can't see my aim people. I have tried to reinstall and all that goody stuff. I looked all over everywhere to find it to come back. I really need my aim people, I have my boss and co-workers contacts on it. 

PLease help, i need this to be back asap.

---

### Post by nphx on 2007-06-28
Have you tried Pidgin, it's the next version of Gaim. The name change due to legal battle with AOL.

**Pidgin 2.0.2** : [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

---

### Post by phizikal on 2007-06-28
I downloaded both files, and installed the data file first. successful.
but on the first one.

"dependency is not satisfiable: libbonobo2-0"

---

### Post by phizikal on 2007-06-28
i also tried getting that dependency.

```
root@admin:/home/admin# sudo apt-get install libbonobo2-0
Reading package lists... Done
Building dependency tree... Done
libbonobo2-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by nphx on 2007-06-28
Try using Synaptic Package Manager, and search for **libbonobo2-0**

Make sure you have your universe repositories enabled.

---

### Post by speaker219 on 2007-06-28
You could try a .deb Pidgin installer:
[http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)
(install pidgin and pidgin-data)

---

### Post by phizikal on 2007-06-28
I reinstalled it using synaptic.
and still it wont install pidgin.
and is it available for dapper?

---

### Post by phizikal on 2007-06-28
*cough*

---

### Post by phizikal on 2007-06-28
no help anyone?

---

### Post by SummerNight on 2007-06-28
Uninstall and then d/l install from here:
[http://linuxappfinder.com/package/gaim](http://linuxappfinder.com/package/gaim)

Or try out kopete, which is kind of like Trillian:
[http://kopete.kde.org/](http://kopete.kde.org/)

Of course that would be sudo apt-get install kopete

---

### Post by bean77 on 2007-07-01
> **phizikal said:**
> Ok, i have msn, aim, and yahoo on gaim. It always was fine until earlier I can't see my aim people. I have tried to reinstall and all that goody stuff. I looked all over everywhere to find it to come back. I really need my aim people, I have my boss and co-workers contacts on it. 

PLease help, i need this to be back asap.

I am having the same issue.

---

