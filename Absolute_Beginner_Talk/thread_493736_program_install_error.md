---
title: "program install error"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Dai777 on 2007-07-06
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I do this ?

thanks Dai

---

### Post by lisati on 2007-07-06
> **Dai777 said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I do this ?

thanks Dai

From the terminal (you can find it on the "Accessories" menu under "Applications"), type:
```

sudo dpkg --configure -a

```
edit: p.s. I'm not sure about the "please report" bit......

---

### Post by Dai777 on 2007-07-06
the problem seems to be skype, but can't unistall it how would I unistall skype manually

---

### Post by Dai777 on 2007-07-06
dai@ubuntu-desktop:~$ sudo apt-get remove skype
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dai@ubuntu-desktop:~$ 
dai@ubuntu-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
dai@ubuntu-desktop:~$ 

need help sorting this out

---

### Post by moredhel on 2007-07-06
sudo dpkg --configure -a

remember the sudo part ;)

---

### Post by Dai777 on 2007-07-06
just keeps bringing up the skype license agreement

no way of accepting it properly so this is screwing up all other installs including updates for linux.
need to uninstall skype or sort this licence out some how.

[[img=http://img442.imageshack.us/img442/1705/screenshotdaiubuntudeskxc6.th.png]](http://img442.imageshack.us/my.php?image=screenshotdaiubuntudeskxc6.png)

---

### Post by moredhel on 2007-07-07
press tab then space bar.

;)

---

### Post by Dai777 on 2007-07-07
cheers looks like it's working again.

---

