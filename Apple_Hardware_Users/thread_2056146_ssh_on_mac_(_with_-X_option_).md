---
title: "ssh on mac ( with -X option )"
date: 2012-09-10
forum: Apple Hardware Users
---

### Post by Kdar on 2012-09-10
On Linux, I would usually use ssh -X user@servername to load application from the server computer I am trying to connect.

How can do the same on mac? Mac is using different windows system, right?

---

### Post by Lars Noodén on 2012-09-11
OS X uses [Quartz](http://www.oreillynet.com/pub/a/mac/2005/10/11/what-is-quartz.html) under its Aqua GUI instead of X.  So that means that you can connect from OS X to a Linux machine and forward X  from the Linux machine to the Macintosh, but not vice versa.  However, you might have to install X11 on the Mac first, depending on whether you did that already or not.  If you need to install X11, check your installation DVD first.

---

