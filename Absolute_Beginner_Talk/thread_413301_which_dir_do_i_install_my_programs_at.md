---
title: "which dir do i install my programs at?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-04-19
because i am used to windows and where they stores their programes in the c:/windows/program files..

in linux where do most people install their programs? i know you can install it in any dir but can someone tell me so at least someone like me follow some kind of standard rule?

---

### Post by aysiu on 2007-04-19
Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by dfox8895 on 2007-04-19
Traditional linux is to never install directly in /bin or /sbin

**Feel Free ** to install in /usr/local/bin or /usr/local/sbin or /opt.

This protects the system, and helps protect data during an upgrade.  /opt is of debian lineage, I believe, and is used for programs that will be used by everyone.  while /usr/local/bin or /usr/local/sbin is for the administrator.   In my opinion, you should use synaptic or debi to install all programs in Ubuntu to ensure that you keep the system "clean".  I would avoid tar.gz, tar.bz until you understand the conflicts that could potentially arise.

---

