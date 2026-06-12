---
title: "change usplash.conf"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by muldengold on 2008-03-13
I need to change the resolution in the usplash.conf (/etc/usplash.conf). However, when I want to save the file I am denied permission to do so, although I have the general permission to administer the system. Where am I wrong?

---

### Post by spiderbatdad on 2008-03-13
To open gedit with sudo permissions:```
gksu gedit /etc/usplash.conf
``` To make changes to the root file system requires that a user with administrative rights become a super user.

---

### Post by muldengold on 2008-03-13
Thanks, it worked!!!

---

### Post by dcstar on 2008-03-14
Any changes to the usplash.conf file will only affect the logout screen unless you load a kernel update or do this:

```
sudo update-initramfs -u
```

---

