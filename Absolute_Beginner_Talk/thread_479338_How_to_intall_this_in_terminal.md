---
title: "How to intall this in terminal"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-20
Hi i have a friend with ubuntu server and no GUI on it....and he needs to install this file [http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.350_all.deb&use_mirror=surfnet]("http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.350_all.deb&use_mirror=surfnet")
How do he do that in terminal??? (need answers fast plz)

---

### Post by hyper_ch on 2007-06-20
```

man dpkg

```

---

### Post by AndyCooll on 2007-06-20
Change to the directory it's been downloaded to, then something like the following should do the trick:

```
sudo dpkg -i package_to_be_installed.deb
```

:cool:

---

### Post by ajmannen on 2007-06-20
> wolfheart@fenriz:/home/disk1/Appz/Progz/server stuff$ sudo dpkg -i webmin_1.350_all.deb
(Reading database ... 34188 files and directories currently installed.)
Preparing to replace webmin 1.350 (using webmin_1.350_all.deb) ...
Unpacking replacement webmin ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
wolfheart@fenriz:/home/disk1/Appz/Progz/server stuff$

HELP

---

### Post by atria on 2007-06-20
Install the dependencies using this command if you need it fixed urgently:

```
sudo aptitude install libnet-ssleay-perl libauthen-pam-perl libio-pty-perl libmd5-perl
```

Do write down what you've installed though, so you can remove them in future when you no longer need webmin.

---

