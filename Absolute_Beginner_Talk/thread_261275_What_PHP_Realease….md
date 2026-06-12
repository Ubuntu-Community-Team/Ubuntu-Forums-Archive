---
title: "What PHP Realease…"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Pure_Acid on 2006-09-20
I have PHP 4.4 installed running on a Open SUSE 10 box, can someone please tell me where I find the latest version for OPEN SUSE?

I am totally new to Ubuntu and I am downloading right now, I am actually a Open SUSE fan and I am running version 10 on our server boxes as well as SLED and SLES 10.

I would like to know what version of MySQL and PHP gets packaged with Ubuntu 6.06 (Dapper Drake)?

Thanks.   ;)

---

### Post by bluefrog on 2006-09-20
in dapper you can have php / mysql 4 and/or 5 straight form the repository.

It's up to you.

James

---

### Post by hw-tph on 2006-09-20
These are the current PHP versions in Ubuntu 6.06:

```
hakan@devon:~$ apt-cache policy php5 php4
php5:
  Installed: (none)
  Candidate: 5.1.2-1ubuntu3.2
  Version table:
     5.1.2-1ubuntu3.2 0
        500 http://security.ubuntu.com dapper-security/main Packages
     5.1.2-1ubuntu3 0
        500 http://archive.ubuntu.com dapper/main Packages
php4:
  Installed: (none)
  Candidate: 4:4.4.2-1build1
  Version table:
     4:4.4.2-1build1 0
        500 http://archive.ubuntu.com dapper/universe Packages
```

Håkan

---

### Post by Pure_Acid on 2006-09-20
> **hw-tph said:**
> These are the current PHP versions in Ubuntu 6.06:

```
hakan@devon:~$ apt-cache policy php5 php4
php5:
  Installed: (none)
  Candidate: 5.1.2-1ubuntu3.2
  Version table:
     5.1.2-1ubuntu3.2 0
        500 http://security.ubuntu.com dapper-security/main Packages
     5.1.2-1ubuntu3 0
        500 http://archive.ubuntu.com dapper/main Packages
php4:
  Installed: (none)
  Candidate: 4:4.4.2-1build1
  Version table:
     4:4.4.2-1build1 0
        500 http://archive.ubuntu.com dapper/universe Packages
```

Håkan

So if you install a LAMP configuration you have the choice of either PHP 4/5? :confused:

---

### Post by hw-tph on 2006-09-20
Yes, you can choose between php4 and php5. Actually, you can have both installed at the same time and configure your web server to use the one you want (if you would want that...).

Håkan

---

