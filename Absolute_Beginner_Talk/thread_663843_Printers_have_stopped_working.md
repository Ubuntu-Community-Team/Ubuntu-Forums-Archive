---
title: "Printers have stopped working"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by JohnMoriarty on 2008-01-10
After a recent update al my printing facilities have vanished. I've tried reinstalling CUPS, with the following results. Any suggestions? Please?

```
johnmoriarty@johnmoriarty:/$ sudo aptitude reinstall cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  cupsys 
The following partially installed packages will be configured:
  cupsys-driver-gutenprint 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cupsys (1.3.2-1ubuntu7.3) ...
ln: accessing `/usr/lib/cups/backend-available/ipp': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys (1.3.2-1ubuntu7.3) ...
ln: accessing `/usr/lib/cups/backend-available/ipp': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done  
```

Thanks
John

---

### Post by Deadmode on 2008-01-10
post the CUPS logs from /var/log/cups

---

### Post by JohnMoriarty on 2008-01-10
In /var/log/cups/ there are a load of .gz files with old logs (nothing from this year) and the printers have worked since these so I presume (correct me if I'm wrong) that these aren't needed.

Apart from these there are access_log, page_log and error_log, all 0 bytes.
page_log and access_log were modified yesterday (when I last printed, I think), and error_log back in December.

I don't know if this helps,
let me know if you need more info,
thanks
John

---

### Post by peabody on 2008-01-10
Judging by [other](http://ubuntuforums.org/showthread.php?t=662423) things this update did, I'd say it's a good chance the snmp update screwed something up.

I think I'll try taking a look at my own printing at home.

---

### Post by JohnMoriarty on 2008-01-12
Problem appears to be fixed. I did complete remove for cupsys (and removed all its dependencies) and then put them back.
Thanks for all the suggestions!
John

---

