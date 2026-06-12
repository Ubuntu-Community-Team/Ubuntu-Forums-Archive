---
title: "File Permissions"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by utab on 2006-10-06
Dear all,

There is a file that I can not execute

this file is under /usr/local/opt/msc/bin

-rwxr-xr-x 17 root root  11420 2004-07-28 15:18 nastran.

When trying to execute ./nastran, I get

bash: ./nastran: /bin/ksh: bad interpreter: No such file or directory 

since I have owner and group permissions as root, I think that is the problem.

Regards,

---

### Post by crane on 2006-10-06
Try changing to that directory
```
cd /usr/local/opt/msc/bin
```then execute with
 ```
sudo nastran
```
id nastran is the name of theexecutable.

---

### Post by GlennB on 2006-10-06
Hi,

> **utab said:**
> Dear all,

There is a file that I can not execute

this file is under /usr/local/opt/msc/bin

-rwxr-xr-x 17 root root  11420 2004-07-28 15:18 nastran.

When trying to execute ./nastran, I get

bash: ./nastran: /bin/ksh: bad interpreter: No such file or directory 

since I have owner and group permissions as root, I think that is the problem.

Regards,

It looks to me as though that file wants to be run using ksh (the korn shell). The default shell in Ubuntu is bash, and there is a strong possibility you don't have the korn shell installed.

You could install a version of the korn shell - there is a public domain version called pdksh, and it should be available through synaptic.

Regards,

Glenn.

---

