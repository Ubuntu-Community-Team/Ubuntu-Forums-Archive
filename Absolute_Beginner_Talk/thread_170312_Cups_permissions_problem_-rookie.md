---
title: "Cups permissions problem -rookie"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by NotGrayt on 2006-05-04
This is my third attempt at setting up Cups in Ubuntu 5.10.  I need to set up a printer throught the Cups Localhost:631, and at the very end I get an error "server error - internal error".  Looking at the cups error log, (/var/log/cups/error.log)  I get

 04/May/2006:08:24:22 -0500 Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7654)
 04/May/2006:08:24:22 -0500 Setting RoHSsp55 device-uri to "socket://172.17.3.62:9100" (was "file:/dev/null".)
 04/May/2006:08:24:22 -0500 Setting RoHSsp55 printer-is-accepting-jobs to 1 (was 0.)
 04/May/2006:08:24:22 -0500 Setting RoHSsp55 printer-state to 3 (was 5.)
** 04/May/2006:08:24:22 -0500 add_printer: Unable to copy PPD file from /usr/share/cups/model/dcc.ppd to /etc/cups/ppd/RoHSsp55.ppd - Permission denied!**
 I have made myself part of the lpadmin group, I've added cupsys to the shadow group, and I've commented out in the /etc/cups/cupsd.conf file the the two lines near the end of the file that say "AuthType Basic" and "AuthClass System".
I have not set up a root password.

Any ideas?

---

