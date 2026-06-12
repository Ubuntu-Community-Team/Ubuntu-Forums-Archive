---
title: "Converting .rpm to .deb packages"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-04-22
I am using alien but I keep getting this error message

```

ubuntu@ubuntu:~/Desktop$ sudo alien LimeWireLinux.rpm
sh: rpm: command not found
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} LimeWireLinux.rpm":  at /usr/local/share/perl/5.8.7/Alien/Package.pm line 466.

```

Does anyone have an alternative or a way to fix this problem?

---

### Post by Ensnared on 2006-04-22
sudo apt-get install rpm

:)

---

### Post by Reggaeton King on 2006-04-22
[PHP]
ubuntu@ubuntu:~/Desktop$ rpm LimeWireLinux.rpm
RPM version 4.0.4
Copyright (C) 1998-2000 - Red Hat, Inc.
This program may be freely redistributed under the terms of the GNU GPL

Usage: rpm {--help}
       rpm {--version}
cledet@ubuntu:~/Desktop$ rpm -i LimeWireLinux.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
ubuntu@ubuntu:~/Desktop$ sudo alien -i LimeWireLinux.rpm
Can't exec "822-date": No such file or directory at /usr/local/share/perl/5.8.7/Alien/Package.pm line 465, <GETPERMS> line 56.
Use of uninitialized value in scalar chomp at /usr/local/share/perl/5.8.7/Alien/Package/Deb.pm line 650, <GETPERMS> line 56.
822-date did not return a valid result. You probably need to install the dpkg-dev debian package at /usr/local/share/perl/5.8.7/Alien/Package/Deb.pm line 652, <GETPERMS> line 56.
[/PHP]

I did install rpm, when I tried to install a .rpm package,it told me to use "Alien"

---

### Post by htinn on 2006-04-22
Make sure you also have the following packages:

debhelper, perl, dpkg-dev, make, cpio

---

### Post by Ensnared on 2006-04-22
[QUOTE=Reggaeton King]I did install rpm, when I tried to install a .rpm package,it told me to use "Alien"[/QUOTE]
Yea, I should have been more elaborate, but it's almost 4 AM so you'll have to excuse me ;)

You're not supposed to use rpm to install the package, buy alien needs rpm to be installed in order to convert the package to a deb. Alien is just a script (think it's perl), which runs external commands, and it used the rpm command to extract information from the rpm-package which it needs to re-pack it as a deb.

So, what I should have said is:
sudo apt-get install rpm
sudo alien LimeWireLinux.rpm

Then install the deb-package it generates :)

EDIT
Erm, yea, just read the rest of the error you posted :P It's still late ;) But install the packages htinn listed and you should be all set.

---

### Post by Reggaeton King on 2006-04-22
needed dpkg-dev...the package converted!

thank guys!

EDIT:

lol  ](*,)

---

