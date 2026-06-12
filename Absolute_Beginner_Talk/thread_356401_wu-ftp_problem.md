---
title: "wu-ftp problem"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by vatzcar on 2007-02-08
i've installed wu-ftpd in my box. when i'm trying to connect from other pcs of my network. in ftp client it's showing an error stating server actively rejecting the connection. how to solve the problem.

---

### Post by ^rooker on 2007-02-08
The info you're giving is a little vague... 

How have you configured wuftpd?
Is the demon "wuftpd" running?
It's probably more interesting what the logs on the server side say (you only told about the clients).

got any firewalling on the clients that might cause the problem? (=check if you can connect locally)

---

### Post by vatzcar on 2007-02-08
thanx for your reply. locally it's also not allowing. i configed wu-ftp with webmin, and i'm very new to it so i haven't messed with it much. the ftpd is running.

---

### Post by ^rooker on 2007-02-09
puh... I've never used webmin for wuftp, so I can't say anything about that.

Are you being rejected by the port already, or with something like "unknown username/password?" - when you telnet to port 21 of that machine, do you get some "hello?"

something like this:
> 220 "Welcome on WUFTP server."
530 Please login with USER and PASS.
221 Goodbye.

However, forget access from other machines unless it works at least locally, too!

If you could provide any further information about your wuftp config, I might be able to help you more (I've already set up wuftp several times, but always manually)

---

### Post by xdefconx on 2008-01-03
> **^rooker said:**
> The info you're giving is a little vague... 

How have you configured wuftpd?
Is the demon "wuftpd" running?
It's probably more interesting what the logs on the server side say (you only told about the clients).

got any firewalling on the clients that might cause the problem? (=check if you can connect locally)

Hye! May i know how to configure/enable wuftpd on ubuntu? i already searching on this forum and also google+yahoo but not really help

---

