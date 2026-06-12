---
title: "Troubles with KDE :("
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-09-05
Hey everyone~

I'm having some troubles with KDE.  I decided to try migrating to KDE from Gnome.  So I downloaded it from the repositories.  Now I have it all up and running.  But I can't change my resolution.  I asked on IRC and they said I needed a menu called "System Settings".  I currently don't have this menu.  They told me to download kubuntu-desktop.  When I try that it says I have some unmet dependencies and that I should do "sudo apt-get -f install".  When I do this I get this error:


```
henaro@henaro-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kate
The following NEW packages will be installed:
  kate
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/811kB of archives.
After unpacking 2302kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 163924 files and directories currently installed.)
Unpacking kate (from .../kate_4%3a3.5.6-0ubuntu20.2_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/kate_4%3a3.5.6-0ubuntu20.2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libkateinterfaces.so.0.0.0')
Errors were encountered while processing:
 /var/cache/apt/archives/kate_4%3a3.5.6-0ubuntu20.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Anyone know how to solve this?

---

### Post by SOULRiDER on 2007-09-05
I used to get errors like this and the problem was that I had run out of HD space. You might wanna double check that.

Also, have you tried with aptitude?
```
sudo aptitude install kate
```

---

### Post by Henaro on 2007-09-05
That returned more errors:


```
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of kdebase:
 kdebase depends on kate (>= 4:3.5.6-0ubuntu20.2); however:
  Package kate is not installed.
dpkg: error processing kdebase (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate-plugins:
 kate-plugins depends on kate (>= 4:3.5.5-1); however:
  Package kate is not installed.
dpkg: error processing kate-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-core:
 kde-core depends on kdebase (>= 4:3.4.3); however:
  Package kdebase is not configured yet.
dpkg: error processing kde-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-amusements:
 kde-amusements depends on kde-core (>= 5:47); however:
  Package kde-core is not configured yet.
dpkg: error processing kde-amusements (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde:
 kde depends on kde-core (>= 5:47); however:
  Package kde-core is not configured yet.
 kde depends on kde-amusements (>= 5:47); however:
  Package kde-amusements is not configured yet.
dpkg: error processing kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdeaddons:
 kdeaddons depends on kate-plugins (>= 4:3.5.6-0ubuntu2); however:
  Package kate-plugins is not configured yet.
dpkg: error processing kdeaddons (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdebase
 kate-plugins
 kde-core
 kde-amusements
 kde
 kdeaddons

```  :mad:

---

### Post by SOULRiDER on 2007-09-05
Do
```
sudo atptitude update
sudo aptitude install kubuntu-desktop
```

see if that helps. Have you checked HD space? If you have a fast conenction I would clean the package cache by doing
```
sudo aptitude clean
```

---

### Post by Henaro on 2007-09-05
> **SOULRiDER said:**
> Do
```
sudo atptitude update
sudo aptitude install kubuntu-desktop
```

see if that helps. Have you checked HD space? If you have a fast conenction I would clean the package cache by doing
```
sudo aptitude clean
```

Worked perfectly, thanks :).

---

### Post by SOULRiDER on 2007-09-05
Thanks great to hear!

---

