---
title: "Please help to get rid of error message"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-06-30
E: oss-linux: subprocess post-installation script returned error exit status 1

That is the error message that i get everytime i install updates or new programs.

Just a bit annoying 

Stephen

---

### Post by Seisen on 2007-06-30
Put this in the terminal

```
sudo dpkg --configure -a
```

---

### Post by halesquad on 2007-06-30
stephen@stephen-desktop:~$ sudo dpkg --configure -a
Password:
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
stephen@stephen-desktop:~$ 


this is what i get

---

### Post by halesquad on 2007-06-30
does anyone know what to do to get rid of this error message?

---

### Post by halesquad on 2007-07-01
where has this error mesage come from and please tell me how to get rid of it.

---

