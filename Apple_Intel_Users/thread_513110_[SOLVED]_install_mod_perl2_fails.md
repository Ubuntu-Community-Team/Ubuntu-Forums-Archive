---
title: "[SOLVED] install mod_perl2 fails"
date: 2007-07-30
forum: Apple Intel Users
---

### Post by cancaseiro on 2007-07-30
Trying to install mod_perl2 but it fails:

```
Please provide a full path to 'apxs' executable
(press Enter if you don't have it installed):  /usr/bin/apxs


[  error] Unable to open /usr/include/apache-1.3/ap_release.h: No such file or directory
[  error] Unable to determine server version, aborting.
[  error] Invalid MP_APXS specified?
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  PGOLLUCCI/mod_perl-2.0.3.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
```

What should I do? ](*,)

---

### Post by cyberdork33 on 2007-07-30
> 
[  error] Unable to open /usr/include/apache-1.3/ap_release.h: No such file or directory
My guess is that you need some apache header files to compile against and they are not installed. Look in the repository for apache packages with '-dev' on the end.

---

### Post by cancaseiro on 2007-07-31
Hi! You might be right as something is wrong with my Apache2 installation because I can't start it:

```
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory
```

I will try to uninstall and then re-install it. :roll:

---

### Post by cancaseiro on 2007-07-31
No use, same answer. Them it. Something is completely wrong and in frustration as last help resort I deleted apache2 folder from /etc/ and now I know it wasn't wisest thing to do. What should I do to restore apache2 directory to /etc?

---

### Post by cyberdork33 on 2007-07-31
> **cancaseiro said:**
> No use, same answer. Them it. Something is completely wrong and in frustration as last help resort I deleted apache2 folder from /etc/ and now I know it wasn't wisest thing to do. What should I do to restore apache2 directory to /etc?

```
$sudo aptitude remove apache2
$sudo aptitude install apache2
```Replace apache2 with the name of the package, whatever it might be, i am just guessing.

---

### Post by cancaseiro on 2007-08-01
> **cyberdork33 said:**
> ```
$sudo aptitude remove apache2
$sudo aptitude install apache2
```Replace apache2 with the name of the package, whatever it might be, i am just guessing.

What package do You mean? I need to restore apache2 directory to /etc/ because I removed it with rm -r command.

---

### Post by cancaseiro on 2007-08-01
Hey I took down apache2.2-common with sudo apt-get remove --purge (packet name) and reinstalled it, that action restored apache2 folder to /etc and everytihing is it was before me removing it from /etc but I still can't understand what is wrong and when I try to install mod-perl2 it doesn't install. Maybe I should configure Apache not Apache2? Problem is still:

```
[  error] Unable to open /usr/include/apache-1.3/ap_release.h: No such file or directory
[  error] Unable to determine server version, aborting.
[  error] Invalid MP_APXS specified?
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  PGOLLUCCI/mod_perl-2.0.3.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 PGOLLUCCI/mod_perl-2.0.3.tar.gz              : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256
```

:x

---

### Post by cancaseiro on 2007-08-01
> **cancaseiro said:**
> What package do You mean? I need to restore apache2 directory to /etc/ because I removed it with rm -r command.

Actually the solution for that problem was easy: ```
sudo apt-get install libapache2-mod-perl2
```

:)

---

### Post by cyberdork33 on 2007-08-01
glad you got it working.

---

