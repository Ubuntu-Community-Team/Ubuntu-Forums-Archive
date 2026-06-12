---
title: "ftp server"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by holsv1 on 2006-11-10
Hi, I have just installed a LAMP server, and now I need to know how to install a ftp server on it.

I have tried ```
sudo apt-get install proftpd
```

but then this just happend: E: Couldn't find package proftpd...

what to do?

---

### Post by taurus on 2006-11-10
You probably need to enable both universe & multiverse in /etc/apt/sources.list.  You can do that by removing the # sign in front of those lines...

```
sudo nano -Bw /etc/apt/sources.list
sudo aptitude update
sudo aptitude install proftpd
```

---

