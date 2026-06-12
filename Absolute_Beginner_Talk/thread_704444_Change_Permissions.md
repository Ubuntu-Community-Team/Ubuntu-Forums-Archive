---
title: "Change Permissions?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-02-22
sudo nautilus doesn't appear to be working.

How can I change the permissions of a folder entitled here.

opt/xampp

I want read/write access to everyone.

---

### Post by taurus on 2008-02-22
Applications -> Accessories -> Terminal
```
sudo chmod -R 777 /opt/xampp
ls -la /opt
```

HOWEVER, you better not run that command for your root filesystem or you will break it.

---

### Post by aysiu on 2008-02-22
*sudo nautilus* or, more appropriately ```
gksudo nautilus
``` isn't for changing permissions but for temporarily gaining more permissions or escalating privileges.

I do believe, however, that with *gksudo nautilus* you should be able to right-click the folder, select Properties and then change ownership of a folder from within that dialogue.

What taurus suggested will work, though.

---

### Post by DaveGiant on 2008-02-22
it was lampp not xampp. My mistake

This comes up.

drwxr-xr-x  3 root  root 4096 2008-02-22 16:55 .
drwxr-xr-x 21 root  root 4096 2008-02-21 16:14 ..
drwxrwxrwx 20 jason root 4096 2008-02-11 08:24 lampp

However nothing changes under the permissions and the folders inside lampp are not modified.

---

### Post by DaveGiant on 2008-02-22
When I run gksudo nautilus I get the following.

> (nautilus:9949): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

---

### Post by aysiu on 2008-02-22
> **DaveGiant said:**
> When I run gksudo nautilus I get the following.
Does the window still launch, or is that the only thing you see?

---

