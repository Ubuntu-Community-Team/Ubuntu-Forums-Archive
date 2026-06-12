---
title: "[SOLVED] HP Deskjet  3820"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-09-22
Hi All

Having trouble installing this printer. My pc does not appear to be detecting this printer.  I believe I am using the parallel port.  Here is the results of lpinfo -v
network socket
network beh
direct hp:/no_device_found
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
network smb


I attempted to add the printer using the gui but I keep running into password issues.

any ideas?

Thanx

Xoanan

---

### Post by linuxwizard on 2007-09-22
According to these links only detection is USB no Parallel port detection. Needs to be setup with USB than should work perfect

[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3820](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3820)

[http://hplip.sourceforge.net/supported_devices/inkjet.html](http://hplip.sourceforge.net/supported_devices/inkjet.html)

---

### Post by Xoanan on 2007-09-23
Thanx;  much obliged

---

