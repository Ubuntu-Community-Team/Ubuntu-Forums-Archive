---
title: "Help with making a Squid Proxy Server on Windows Vista 32Bit"
date: 2012-07-19
forum: Any Other OS
---

### Post by TheMainVein on 2012-07-19
Hello I'm trying to create a squid proxy server and I keep getting this error.. what am i doing wrong?


C:\Windows\system32>cd /d c:\squid

c:\squid>copy etc\*.default etc\*.
etc\cachemgr.conf.default
Overwrite etc\cachemgr.conf.? (Yes/No/All): No
etc\mime.conf.default
Overwrite etc\mime.conf.? (Yes/No/All): No
etc\squid.conf.default
Overwrite etc\squid.conf.? (Yes/No/All): No
etc\squid_radius_auth.conf.default
Overwrite etc\squid_radius_auth.conf.? (Yes/No/All): No
0 file(s) copied.

c:\squid>net start squid
The requested service has already been started.

More help is available by typing NET HELPMSG 2182.


c:\squid>c:\squid\sbin\squid.exe -k reconfigure -n Squid
FATAL: ERROR: cache_peer xxx.xxx.1.3 specified twice

Squid Cache (Version 2.7.STABLE8): Terminated abnormally.
CPU Usage: 0.047 seconds = 0.000 user + 0.047 sys
Maximum Resident Size: 3624 KB
Page faults with physical i/o: 913

abnormal program termination

c:\squid>

---

### Post by sffvba[e0rt on 2012-07-19
*Thread moved to **Other OS/Distro Talk**.*


404

---

