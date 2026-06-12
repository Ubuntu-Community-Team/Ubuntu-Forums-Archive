---
title: "Trouble with apt-get install"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-09-19
Hey there everyone,

When I try to use this command:

sudo apt-get install openrpg

I get this error in my konsole and it does not finish installing:

0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   723  100   723    0     0   3692      0 --:--:-- --:--:-- --:--:--  117k
Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum f75a060f25225d1c920f85a946818301.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone had this trouble before?
~J3ff

---

### Post by gautada on 2007-09-19
Seems to be a heardware crypto issue with the broadcom chip but also the MD5 sum for the file is off...  Sorry I have no idea how to fix.

---

