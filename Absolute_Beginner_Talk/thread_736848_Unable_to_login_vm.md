---
title: "Unable to login vm"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Will_00 on 2008-03-27
I have recently downloaded VM and Ubuntu associated with it. Ubuntu loads, except it only gets to the login screen. I am unable to login using the username: jars and password: jars - I use Windows mainly, so Ubuntu is different. Could someone assist?

---

### Post by wormser on 2008-03-27
You can boot into recovery mode and change the password.  Hit Esc on boot the select recovery mode.  Then run the following command.

```
passwd username
```

The user name is whatever it is suppose to be.  Next reboot with:

```
reboot
```

You should be able to log in now.  In case the user name is wrong, run:

```
ls -la /home
```

The folders are the user names.

---

