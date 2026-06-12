---
title: "Error installing package proftpd on 6.10 Edgy"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by johnk300 on 2006-11-08
Following Ubuntu Guide, tried to install FTP server with:

>sudo apt-get install proftpd

Failed with error "E: Couldn't find package proftpd"

Solution:

Installed GUI Administration program "gproftpd" instead:

>sudo apt-get install gproftpd

gproftpd must have dependency on proftpd, as it also installs server package successfully as well.

To configure proftpd:

>sudo gproftpd

---

### Post by localuser on 2006-11-08
Try this...

System | Administration | Software Sources

Add the universe and multiverse repositories then retry to install it.

---

