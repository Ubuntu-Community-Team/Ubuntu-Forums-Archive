---
title: "[SOLVED] Need Command to view linux distro"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-07-26
I'm sure this may have been answered but I didn't know how to search for it. 
Can anyone tell me how to check which version of Ubuntu (or which distro of Linux in general) installed on a machine? uname -a didn't really tell me much besides kernel version. Thanks.

---

### Post by felicity on 2007-07-26
I'm not sure about a command from the terminal, but in Ubuntu you can check by the System > About Ubuntu menu.

---

### Post by RomeReactor on 2007-07-26
Hi. In Ubuntu you run this command:
```
cat /etc/issue
```
As for other distros, I can't assure you the same command would work.

---

### Post by jfinkels on 2007-07-26
> **aspen_dv said:**
> I'm sure this may have been answered but I didn't know how to search for it. 
Can anyone tell me how to check which version of Ubuntu (or which distro of Linux in general) installed on a machine? uname -a didn't really tell me much besides kernel version. Thanks.

Try this:```
cat /etc/issue
```

EDIT: nice, RomeReactor. :D

---

### Post by nyinge on 2007-07-26
> **aspen_dv said:**
> I'm sure this may have been answered but I didn't know how to search for it. 
Can anyone tell me how to check which version of Ubuntu (or which distro of Linux in general) installed on a machine? uname -a didn't really tell me much besides kernel version. Thanks.
```
 cat /etc/lsb-release 
```
works too, but I'm not sure if that will work for older releases which are not lsb certified.

---

### Post by aspen_dv on 2007-07-26
cat /etc/issue 
Thanks

---

