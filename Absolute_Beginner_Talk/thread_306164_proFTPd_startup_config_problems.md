---
title: "proFTPd startup config problems"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-11-24
Hi, I thought I could sort this out, but am stuck.
Am getting the following errors trying to run proftpd :-
```
ian@homer:/home$ sudo proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - parsing '/etc/proftpd/modules.conf' configuration
 - mod_tls/2.1.1: using OpenSSL 0.9.8b 04 May 2006
 - DenyFilter: compiling deny regex '\*.*/'
 - <IfModule>: using 'mod_tls.c' section at line 65
 - <IfModule>: skipping 'mod_quota.c' section at line 69
 - <IfModule>: skipping 'mod_ratio.c' section at line 73
 - <IfModule>: using 'mod_delay.c' section at line 81
 - <IfModule>: using 'mod_ctrls.c' section at line 85
 - mod_ctrls/0.9.4: closing ctrls socket '/var/run/proftpd/proftpd.sock' (3)
 - <IfModule>: skipping 'mod_ctrls_admin.c' section at line 93
 - <Directory /home/ftp-shared>: deferring resolution of path
 - <Directory /media/share/media/music>: deferring resolution of path
 - IPv4 getaddrinfo 'homer' error: Name or service not known
 - warning: unable to determine IP address of 'homer'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
```

I just want a share, to /media/share/media/music.
And maybe a upload area, but that can come later!

---

### Post by kelbizzle on 2006-11-26
I didn't see a bind directive. or a masquerade adress. 
 
try setting up according to [this]("http://www.proftpd.org/localsite/Userguide/linked/x862.html"). it worked for me.

---

