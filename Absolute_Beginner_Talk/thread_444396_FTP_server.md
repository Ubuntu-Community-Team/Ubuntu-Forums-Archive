---
title: "FTP server"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-05-15
Hi, I have a trouble with my Linux ubuntu, I want to set a FTP server but I don't know how,

Sombody know how can I set a FTP server in Ubuntu?

Thanks

---

### Post by taurus on 2007-05-15
```
sudo aptitude update
sudo aptitude install proftpd gproftpd
gksudo gproftpd
```
And configure it, proftpd,  for your machine.

---

### Post by Kobalt on 2007-05-15
Check this out : [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by echo $USER on 2007-05-15
[http://easylinux.info/wiki/Ubuntu:Feisty#FTP_Server](http://easylinux.info/wiki/Ubuntu:Feisty#FTP_Server)

my personal favorite is vsftpd though

---

