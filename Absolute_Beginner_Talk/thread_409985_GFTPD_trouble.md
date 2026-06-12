---
title: "GFTPD trouble"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-04-15
Hey guys!

I wanna set my ftp like i had it on XP. I use GFTPD a graphical way. I managed to get top some point where FTP seems to work but still cant connect. 

I tested FTP trough [http://www.g6ftpserver.com/en/ftptest](http://www.g6ftpserver.com/en/ftptest) and it gives me this: 

```
Connected to vandorius.dyndns.org (89.212.24.248) port 21
< 220 My FTPD

> USER testing
< 331 Password required for testing.

> PASS *****
< 230-Welcome to "My FTPD" testing
<
< You are user 1 out of a maximum of 5 authorized logins.
< Current time is Sun Apr 15 13:09:09 2007.
< The administrator can be reached here: Admin@this.domain.topdomain
<
<
< Top 10 Uploaders:
< _________________
<
< Top 10 Downloaders:
< ___________________
<
<
< Generated on Wed Apr 11 14:29:05 CEST 2007
<
< 230 Anonymous access granted, restrictions apply.

> PWD
< 257 "/" is current directory.
* Entry path is '/'

> CLNT Testing from http://www.g6ftpserver.com/ftptest from IP 89.212.24.248
< 500 CLNT not understood
* QUOT command failed with 500
* Connection #0 to host vandorius.dyndns.org left intact

* Closing connection #0

```

If anyone knows what CLNT means i wuld be happy to hear it. And one more thing. How do u check if u have some other FTP server running?

---

### Post by thelinuxguy on 2007-04-15
> **Vandorius said:**
> How do u check if u have some other FTP server running?

```

ps -A 

```

should show you all processes. And any FTP daemons running should be listed.

EDIT: 
```

ps -A | grep 'ftp'

```
could be of help

---

