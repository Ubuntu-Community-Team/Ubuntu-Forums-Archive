---
title: "How to setup proFTPd jail account to: /var/www ???"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by hartnady on 2006-01-30
Okay, so, installed proFTPd.

I know how to set up a user jail account to access user's home directory by editing /etc/proftpd.conf.
I know how to set up an annonymous account to access any folder by editing /etc/proftpd.conf.

But... how can I set up an account to be jailed into Apache's /var/www directory? I don't want an anonymous FTP account, it must be password protected.

Any help? Thanks in advance.

---

### Post by BenTyreman on 2006-01-30
Can't you add a new user, specifying the home directory using
```
adduser --home /var/www --no-create-home <user>
```

---

