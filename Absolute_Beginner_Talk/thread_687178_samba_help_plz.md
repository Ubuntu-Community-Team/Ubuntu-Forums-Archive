---
title: "samba help plz"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Foxfire on 2008-02-04
when I try to share files with my laptop to my desktop this happens  Both are running gusty


Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
	Permission denied
Error loading services.


what does this mean ?

---

### Post by spiderbatdad on 2008-02-04
maybe try sudo testparm. or post your smb.conf...possibly your share access does not have correct permissions.

---

### Post by ruy_lopez on 2008-02-04
Check the permissions for /etc/samba/smb.conf are correct. They should be:


```
-rw-r--r-- root root smb.conf
```

---

### Post by spiderbatdad on 2008-02-04
```
sudo chmod 0755 /etc/samba/samba.conf
```actually i think it needs to be executable and r/w so...rwxr-xr-x

---

