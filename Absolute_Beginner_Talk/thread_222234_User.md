---
title: "User"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-07-24
I notice there is an HLIP user listening at port 32770 and 32771. I am wondering whether this is a legitimate user. Therefore, I check the /etc/passwd file and see there is a user HLIP

hplip:x:108:7:HPLIP system user,,,:/var/run/hplip:/bin/false

However, I am still not sure what to do with that information. My question is how can we be sure that a user is a legitimate user?

Thank you.

---

### Post by mlind on 2006-07-24
It's a printer daemon. Nothing to worry about. hplip package installs this, see *aptitude show hplip*.

This user is used by hplip initscript, /etc/init.d/hplip.

---

### Post by mumebuhi on 2006-07-25
Thank you, mlind. That helps.

I have one more question. What else can we do to find out about a user? I have a 'games' user with 'games' group. 

$ aptitude show games
unable to locate package games.

There is also no 'games' user in System -> Administration -> Users and Groups.

---

### Post by mlind on 2006-07-25
> **mumebuhi said:**
> Thank you, mlind. That helps.

I have one more question. What else can we do to find out about a user? I have a 'games' user with 'games' group. 

$ aptitude show games
unable to locate package games.

There is also no 'games' user in System -> Administration -> Users and Groups.

If you tick the "Show all users and groups" checkbox, you'll see the hidden users too. *nix based systems have these useraccounts for certain processes (daemons) to run on background with very limited privileges.

If you look at /etc/passwd (*cat /etc/passwd*), you'll find all users, their groups, home directories and login shells.



User account that Apache HTTPD process runs on (maybe others too)
```

www-data:x:33:33:www-data:/var/www:/bin/sh

```
[LIST]
[*]www-data is username
[*]x is encrypted password
[*]first 33 is user-id ($UID)
[*]second is default group id ($GID), see /etc/group
[*]then home dirctory
[*]login shell
[/LIST]

If login shell is /bin/false, then interactive logins are not allowed.

---

### Post by mumebuhi on 2006-07-25
Thank you mlind!

---

