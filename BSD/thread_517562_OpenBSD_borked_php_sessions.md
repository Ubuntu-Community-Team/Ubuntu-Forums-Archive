---
title: "OpenBSD borked php sessions"
date: 2007-08-04
forum: BSD
---

### Post by mrpeenut24 on 2007-08-04
I'm in the process of making a php-based website for my college's chemistry department that will catalog all of their chemicals and I'm using Folke Asheberg's [php barcode scripts]("http://www.ashberg.de/php-barcode/") to create barcodes based on EANs.  I'm using sessions to control logins and storing user information pulled from mysql.

Everything works perfectly (so far) on Ubuntu, but when I transfer the scripts over to the OpenBSD server we're running it on, the sessions get lost when I transfer pages.  Does anyone have any experience programming php with sessions on OpenBSD that they could shed some insight?  Or perhaps a php.ini file?

(what happens)  I can log in on the log in page, but when I click on the link to the main page, it tells me I'm not logged in, so when I click back on the log in page, it also tells me I'm not logged in.  I'm assuming that the session just isn't being stored, but it is on Ubuntu, so it's most likely not a problem with my scripts.

Anyone have some insight?

---

### Post by mips on 2007-08-05
I do not have an solution for you but if you don't get any responses maybe try here:

[http://www.bsdforums.org/forums/](http://www.bsdforums.org/forums/)
[http://www.nabble.com/OpenBSD-f12601.html](http://www.nabble.com/OpenBSD-f12601.html)

---

