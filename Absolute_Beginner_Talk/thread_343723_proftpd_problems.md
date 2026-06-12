---
title: "proftpd problems"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ansem227 on 2007-01-21
ok, I've never used any forum of Linux before December, and i've been trying to setup a apache 2 and a ftp sever. my apache sever is working amazingly for such a crappy computer i'm using. but on the other hand my ftp sever i cant even get up. I've looked around and my tutorials, I've been to proftpds site, and i've used a few different configuration files, given to me by a friend who's better then me and Linux and i cant get it up. I'm not shore if this will help but this is what it tells me;

```
220 ProFTPD 1.3.0 Server (Debian) [192.168.1.101]
500 GET not understood
500 HOST: not understood
500 USER-AGENT: not understood
550 text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5: Forbidden command argument
500 ACCEPT-LANGUAGE: not understood
500 ACCEPT-ENCODING: not understood
500 ACCEPT-CHARSET: not understood
500 KEEP-ALIVE: not understood
500 CONNECTION: not understood
421 Login Timeout (300 seconds): closing control connection.
```

---

### Post by kidders on 2007-01-22
Hi there,

Assuming these are error messages from your FTP server logs, you seem to be talking HTTP to it. You need to use FTP-capable software to communicate with an FTP server.

---

### Post by ansem227 on 2007-01-22
ok, thanks.
i got it working

---

