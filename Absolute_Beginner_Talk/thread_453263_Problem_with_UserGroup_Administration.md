---
title: "Problem with User/Group Administration"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by timr92 on 2007-05-24
My Users & Groups interface in the System > Administration menu is not working. When i click on it, it asks for my password, which i give it, but then it says "Failed to run users-admin as user root"

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Any ideas?

---

### Post by pouns on 2007-05-24
Hi,
maybe the user you are using is not admin.
Open a terminal, switch to root (su) and try to launch the app (users-admin).

---

### Post by timr92 on 2007-05-24
timothy@ubuntu-lap01:~$ su
Password: 
su: Authentication failure
Sorry.

Is that what i was ment to do?

---

### Post by eldepeche on 2007-05-24
By default, Ubuntu doesn't let you use su. You need to type ```
sudo su -
```

---

### Post by timr92 on 2007-05-25
I don't get it. Can someone tell me step by step exactly what i need to do. I am very much just a beginner.

---

### Post by zhinker on 2007-05-28
I tried to do that but i get this error:

The configuration could not be loaded
You are not allowed to access the system configuration

In case it affects anything, I'm running Xubuntu FIesty

---

### Post by zhinker on 2007-05-28
btw, this was my terminal entry:

rizvi@ubuntu:~$ sudo su -
Password:
rizvi@ubuntu:~$ users-admin

---

