---
title: "Removing Email Server from Ubuntu Server"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by kleptos on 2007-11-14
I dont know if this is in the right spot so bear with me. 

I recently installed ubuntu server on a fresh install and i picked the 'lamp server' and the 'email server' options during startup. I want to remove all the traces of the email components. How can i do this? I tried to use 'apt-get remove' but it cant find the packages which i see running dovecot. It tells me dovecot is not installed so it cant remove it. How can i remove it?
Thanks...


```
 
 4109 dovecot   15   0  3460 1532 1284 S  0.0  1.2   0:00.04 pop3-login
 4110 dovecot   15   0  3464 1528 1284 S  0.0  1.2   0:00.03 pop3-login
 4111 dovecot   15   0  3460 1528 1284 S  0.0  1.2   0:00.04 pop3-login
 4112 dovecot   15   0  3464 1528 1284 S  0.0  1.2   0:00.02 imap-login
 4113 dovecot   15   0  3464 1528 1284 S  0.0  1.2   0:00.02 imap-login
 4114 dovecot   15   0  3468 1532 1284 S  0.0  1.2   0:00.09 imap-login

```

---

