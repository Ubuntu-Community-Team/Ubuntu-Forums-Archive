---
title: "proxy setup ????"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-15
how do u setup a proxy in ubuntu already try the one in system-->preference--->network proxy 
and have ftp-proxy installed [ftp://ftp.suse.com/pub/projects/proxy-suite/src](ftp://ftp.suse.com/pub/projects/proxy-suite/src) but don't know how to use it 
i just want to setup a normal proxy for downloading stuff like in megaupload so i don't have to wait for 3 hours after the download limit existed any clue or help that u can help me 
i think proxy will work but can u guys help me set it up

---

### Post by briealeida on 2007-05-16
Try Squid.

apt-get install squid
 is the command that you issue. I may have switched them around and it may be 
apt-get squid install.

It's very straightforward from there. For configuration, see [www.squid-cache.org](www.squid-cache.org).

Best of luck.

---

### Post by echo $USER on 2007-05-16
I use tinyproxy.  It doesnt cache, just straight proxy.

sudo apt-get install tinyproxy

The config file is at /etc/tinyproxy/*

---

### Post by zerobinary on 2007-05-16
zerobinary@zerobinary:~$ squid
FATAL: Unable to open configuration file: /etc/squid/squid.conf: (13) Permission denied
Squid Cache (Version 2.6.STABLE5): Terminated abnormally.
CPU Usage: 0.004 seconds = 0.000 user + 0.004 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
tinyproxy: Could not open file /var/log/tinyproxy.log: Permission denied
tinyproxy: Could not create log file.
zerobinary@zerobinary:~$ sudo tinyproxy
zerobinary@zerobinary:~$ su zerobinary
Password: 
zerobinary@zerobinary:~$ tinyproxy
tinyproxy: Could not open file /var/log/tinyproxy.log: Permission denied
tinyproxy: Could not create log file.
i try go to etc/tinyproxy but still i don't get how to configure it can u simplify ur explaination

---

### Post by wormser on 2007-05-16
It looks like permission errors.  Try putting sudo before the command.

```
sudo squid
```

---

### Post by zerobinary on 2007-05-17
zerobinary@zerobinary:~$ sudo squid
Password:
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE5): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.008 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 12
Aborted (core dumped)

---

### Post by echo $USER on 2007-05-18
Here is a link that explians setting up tinyproxy...

[http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy](http://ubuntuforums.org/showthread.php?t=122011&highlight=tinyproxy)

---

