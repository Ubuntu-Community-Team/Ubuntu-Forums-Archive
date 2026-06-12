---
title: "In need of Libssl 0.9.7"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-11-29
As the title implies, does anyone know where I can get lissl 0.9.7?  I have tried forcing it through apt-get and I have had 0 success.  I am trying to upgrade to the newest Nessus client and I keep getting this error when running "sudo dpkg -i  Nessus-3.0.6-debian3_i386.deb"

> 
(Reading database ... 149768 files and directories currently installed.)
Preparing to replace nessus 3.0.6 (using Nessus-3.0.6-debian3_i386.deb) ...
$Shutting down Nessus : .
Unpacking replacement nessus ...
dpkg: dependency problems prevent configuration of nessus:
 nessus depends on libssl0.9.7 (>= 0.9.7e); however:
  Package libssl0.9.7 is not installed.
dpkg: error processing nessus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nessus


Any help is greatly appreciated.  Thank you.

---

### Post by RomeReactor on 2007-11-29
Hi. Maybe the [Debian Lenny]("http://packages.debian.org/libssl0.9.7") package could work, or perhaps the [Feisty]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libssl&searchon=names&subword=1&version=all&release=all") package.

---

### Post by hyper_ch on 2007-11-29
or compile nessus yourself...

---

