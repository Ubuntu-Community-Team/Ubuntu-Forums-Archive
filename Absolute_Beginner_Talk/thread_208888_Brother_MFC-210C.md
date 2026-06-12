---
title: "Brother MFC-210C"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-04
Hey

I currently have a Brother MFC-210C USB Printer.

Can someone step me through installing it on Ubuntu?

---

### Post by Jagot on 2006-07-04
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html)

---

### Post by KrisDwyer on 2006-07-08
> **Jagot said:**
> [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html)
When I install the LPR driver i get this!
> root@corolla:/home/kris/Desktop # dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
(Reading database ... 58001 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC210C': No such file or directory
chown: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC210C': No such file or directory


It then drops back to the terminal.

When installing the CUPS driver, I get this;
> root@corolla:/home/kris/Desktop # dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb
Selecting previously deselected package cupswrappermfc210c.
(Reading database ... 58001 files and directories currently installed.)
Unpacking cupswrappermfc210c (from cupswrappermfc210c_1.0.0-1_i386.deb) ...
Setting up cupswrappermfc210c (1.0.0-1) ...

 ****** ERROR: csh is required. ******



Now i'm assuming the CUPS one is due to no cshell. If thats the case how do i get it?

---

### Post by KrisDwyer on 2006-07-08
Anybody?

---

### Post by bigken on 2006-07-08
use bobsongs thread it works a treat ;)[http://www.ubuntuforums.org/showthread.php?t=105703](http://www.ubuntuforums.org/showthread.php?t=105703)

---

### Post by bigken on 2006-07-09
> **KrisDwyer said:**
> When I install the LPR driver i get this!


It then drops back to the terminal.

When installing the CUPS driver, I get this;


Now i'm assuming the CUPS one is due to no cshell. If thats the case how do i get it?
sudo apt-get install csh;)

---

