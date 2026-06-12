---
title: "sudo &amp; sendmail error on startup"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-04-27
---------------------------------------------------------------------------- 
ERROR:
-sudo: unable to lookup server1.example.com /bin/hostname -F via gethostbyname()
 -sendmail: fatal: could not find any active network interfaces

----------------------------------------------------------------------------
WHATiDid:
-configured static ip. installed apache mysql sendmail postfix etc.
-used dhcp to accomplish this b/c initially i couldn't get a connection, not until some time w/ my static ip address. 

----------------------------------------------------------------------------
ProBlem:
-can't make any connection whatsoever statically nor can i use gnome properly b/c server1.example.com path cant' be established.

-------------------------------------------------------------------------
ADDITIONAL INFO:
-so far i've check /etc/networking/interfaces //nothing
-also check /etc/hosts //nothing
-tried /etc/resolve.conf //nothing
-check dns server 64.233.167.99 //access denied

-------------------------------------------------------------------------
Please help if you can. I'm sure his is a noob mistake, but one i'll be glad to learn and never make again.

---

### Post by N3wtR0ckn13 on 2006-05-05
[QUOTE=N3wtR0ckn13]---------------------------------------------------------------------------- 
ERROR:
-sudo: unable to lookup server1.example.com /bin/hostname -F via gethostbyname()
 -sendmail: fatal: could not find any active network interfaces

----------------------------------------------------------------------------
WHATiDid:
-configured static ip. installed apache mysql sendmail postfix etc.
-used dhcp to accomplish this b/c initially i couldn't get a connection, not until some time w/ my static ip address. 

----------------------------------------------------------------------------
ProBlem:
-can't make any connection whatsoever statically nor can i use gnome properly b/c server1.example.com path cant' be established.

-------------------------------------------------------------------------
ADDITIONAL INFO:
-so far i've check /etc/networking/interfaces //nothing
-also check /etc/hosts //nothing
-tried /etc/resolve.conf //nothing
-check dns server 64.233.167.99 //access denied

-------------------------------------------------------------------------
Please help if you can. I'm sure his is a noob mistake, but one i'll be glad to learn and never make again.[/QUOTE]


these errors were the result of a lost static ip connection. thanks

---

