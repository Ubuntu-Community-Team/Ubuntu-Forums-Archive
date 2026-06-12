---
title: "webmin on 5.10 = http error 403"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by bjergtrolden on 2005-12-30
On a Ubuntu server 5.10-64 I have installed webmin by "apt-get install webmin". I can start and stop webmin, I can se its running by "ps -ef" and I can se its "LISTEN" on port 10000 by "netstat -a" - BUT I cant connect to it from a browser from another pc "https://10.0.0.22:10000" sipmly retruns "HTTP error 403 - You are not authorized to view this page"
The server and the pc is connected dirctly - just a HUP - no firewall or .....

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=bjergtrolden]On a Ubuntu server 5.10-64 I have installed webmin by "apt-get install webmin". I can start and stop webmin, I can se its running by "ps -ef" and I can se its "LISTEN" on port 10000 by "netstat -a" - BUT I cant connect to it from a browser from another pc "https://10.0.0.22:10000" sipmly retruns "HTTP error 403 - You are not authorized to view this page"
The server and the pc is connected dirctly - just a HUP - no firewall or .....[/QUOTE]
By default, webmin is configured to reject all requests that don't originate from the local machine.  Try logging on to webmin locally and see if you can find the config option to allow you to log on from a remote destination.

---

### Post by bjergtrolden on 2005-12-30
Thanx
In the file miniserv.conf there are a line starting with "allow=...."
After adding the client ip its working ...

---

