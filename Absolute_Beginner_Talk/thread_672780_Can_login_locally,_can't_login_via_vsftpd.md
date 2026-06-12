---
title: "Can login locally, can't login via vsftpd"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by WNxCryptic on 2008-01-20
I'm trying to setup a development server for my web work and I've gotten everything installed and configured except ftp.

I've installed vsftp and configured it for local logins and whatnot. I wanted an account who's home directory was /var/www and I couldn't do that with an already existing account, so I preformed the following command:

```
useradd -d /var/www ftp
sudo passwd ftp
```

I setup the password.

Long story short I can login via SSH but not via FTP.

---

### Post by WNxCryptic on 2008-01-20
bump?

---

