---
title: "Starting INETD daemon"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by percival95 on 2006-02-13
When trying to start SWAT the instructions say to kill -1 inet daemon. As far as I can tell there is no INET daemon running. How do I start it? Webmin also fails at this task. The message from webmin is that there is nothing to kill.

---

### Post by merlindahapypig on 2006-02-13
it may not be installed, i had this problem the other day when installing swat on a server install of 5.10

apt-get install xinetd

---

### Post by EkaÏnfinitos on 2008-04-19
Had the same trouble occur while installing VMware Server on an otherwise vanilla Edgy; couldn't kill the inetd process because it wasn't there. Installing xinetd cured the woes and worked beautifully with VM Server and the ensuing VM Management Iinterface install.

---

