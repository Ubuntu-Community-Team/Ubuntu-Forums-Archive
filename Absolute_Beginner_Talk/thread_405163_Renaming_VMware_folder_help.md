---
title: "Renaming VMware folder help"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cybrkup on 2007-04-09
While trying to solve a permissions problem with VMWare server I renamed the folder to "vmware.orig". Now I can't run vmware server so I need to change the folder name from vmware.orig back to plain old vmware, but I can't get it to work. Help, please! 

> james@linux-home:/usr/lib$ sudo mv vmware.orig vmware
mv: cannot overwrite non-directory `vmware' with directory `vmware.orig'


---

### Post by taurus on 2007-04-09
Is there already a file/directory vmware in /usr/lib?

```
ls -la /usr/lib
```

---

### Post by cybrkup on 2007-04-09
> **taurus said:**
> Is there already a file/directory vmware in /usr/lib?

```
ls -la /usr/lib
```

No, there isn't:

drwxr-xr-x   2 root root     4096 2007-03-18 13:17 tls
drwxr-xr-x   2 root root     4096 2006-10-25 10:36 upstart
drwxr-xr-x   2 root root     4096 2006-10-25 10:43 usplash
drwxr-xr-x   2 root root     4096 2006-10-25 10:36 valgrind
drwxr-xr-x  17 root root     4096 2007-02-12 13:50 vmware.orig
drwxr-xr-x   3 root root     4096 2007-03-17 12:33 w3m
drwxr-xr-x   6 root root     4096 2006-10-25 10:38 X11
drwxr-xr-x   3 root root     4096 2007-02-15 21:23 xchat

I was following instructions posted on a website to fix the previous problem, so I'm not really sure how I deleted the primary vmware folder to begin with.  ;(

---

### Post by cybrkup on 2007-04-09
.

---

### Post by cybrkup on 2007-04-09
Figured it out. Used CHOWN to set myself as the owner of the folder and then renamed it, then set ownership back to Root.

---

