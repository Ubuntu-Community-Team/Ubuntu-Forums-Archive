---
title: "Replace xorg.conf"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-12-02
Hi,

I have managed to stuff up my xorg.conf, and there is no xorg.conf~ file.  Where can I get an original xorg.conf file to replace my old one?

Thankyou.

---

### Post by IYY on 2006-12-02
The xorg.conf file differs from one machine to another, so we can't just give it to you. Your best bet is to run the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the steps it gives you.

---

### Post by Shatrat on 2006-12-02
Even if there isnt an xorg.conf~ there should be an xorg.conf.backup and an xorg.conf.backup_20061104 which is a backup with the date attatched.
You have to be really rm happy to get rid of all your backed up xorg.conf files.

---

