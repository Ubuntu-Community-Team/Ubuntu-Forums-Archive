---
title: "Error during CUPS"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2008-02-16
Hi All

I am attempting to install a printer on a friends machine and I am getting this error

> There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.

Any thoughts?

:popcorn:

---

### Post by spiderbatdad on 2008-02-16
check you /etc/cupsd.conf file for anything that doesn't look right. You should be able to find the right section to change. Are you trying to use a network printer?  You can search for examples of cupsd.conf files, as well. And make sure you connecting to localhost:631

---

