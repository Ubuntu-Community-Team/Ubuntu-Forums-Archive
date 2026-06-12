---
title: "Printer problems: Can't access localhost:631"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Jakob Rasmussen on 2006-05-25
I've been trying to install a printer (Brother HL 5030) without any luck, but I'm beginning to suspect the problem is rather serious, not just missing drivers or anything like that. 

My progress so far (none, really):

Located printer on the USB-port.
Installed missing and updated existing cups & foomatic files.
Cannot access the cups manager / server via system/administration/printing.
Cannot get in touch with localhost:631 via browser.
"netstat -tl" cannot locate cups server.
"/etc/init.d/cupsys restart" restarts cupsys ok, but no effect.
/var/log/cups/error_log: "StartListening: Unable to bind socket for address [localhost]:631"
cupsd.conf: "Listen [localhost]:631" present

A friend of mine helped, but I'm like totally stuck ](*,)

---

### Post by Sef on 2006-05-25
> I've been trying to install a printer (Brother HL 5030) without any luck 

System > Administration > Printing

Is it there in Breezy?  It is in Dapper.  If it is not in Breezy, then you should upgrade to Dapper, which is in RC1.  It will be stable 1 June.

---

### Post by Jakob Rasmussen on 2006-05-25
As I wrote earlier, I tried that already: "Cannot access the cups manager / server via system/administration/printing". May try Dapper anyway, though.

My problem is, I simply can't seem to get any contact with the cups server.

---

### Post by Sef on 2006-05-25
> As I wrote earlier, I tried that already: "Cannot access the cups manager / server via system/administration/printing". May try Dapper anyway, though.

My problem is, I simply can't seem to get any contact with the cups server.

:oops: sorry I missed that.

---

