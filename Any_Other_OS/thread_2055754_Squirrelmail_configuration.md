---
title: "Squirrelmail configuration"
date: 2012-09-10
forum: Any Other OS
---

### Post by ludo1960 on 2012-09-10
Hello,

I have installed postfix/dovecot/squirrelmail following a tutorial here: [http://linuxadminatoz.blogspot.co.uk...h-postfix.html]("http://linuxadminatoz.blogspot.co.uk/2011/04/debian-mail-server-setup-with-postfix.html")

Using webmin I can send and receive mail from my system users so I guess  the postfix and dovecot configurations are correct, however when I try  to access squirrelmail I get "Unknown user or password incorrect."  

Also when I try to access mysite.com/squirrelmail/src/configtest.php I get:

You don't have permission to access /squirrelmail/src/configtest.php on this server.

The mail log gives this error:
 
Sep 10 06:50:47 debian-squeeze-base dovecot: auth-worker(default):  pam(cliff,127.0.0.1): pam_start() failed: Critical error - immediate  abort
Sep 10 06:50:54 debian-squeeze-base dovecot: imap-login: Aborted login  (auth failed, 1 attempts): user=<cliff>, method=PLAIN,  rip=127.0.0.1, lip=127.0.0.1, secured

I'm guessing it's a permissions issue, attached are the current settings  for POP / IMAP mail server, does this look correct to you guys?

---

