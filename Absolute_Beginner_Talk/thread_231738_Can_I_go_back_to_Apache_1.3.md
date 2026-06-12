---
title: "Can I go back to Apache 1.3?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Hawkowl on 2006-08-07
I'm having a ton of trouble trying to set up vitrual hosts with Apache2, I already have 30 on my old windows/apache1.3 setup running fine.
I can't even get Apache2 to load.
I bought a brand new box specifically to have a go at running linux.
I have spent literally days now, trying to get this server to work.
I have had some great help from you guys, but as yet to no avail.](*,) 
(for full details see thread "virtual host problems") back a page or 2

Anyway can i remove Apache2 and reinstall Apache 1.3?

---

### Post by arjun.shankar on 2006-08-08
Yes.

Type these at the terminal:

Remove apache2 and all related and configuration files:
**sudo apt-get remove --purge apache2**

Install apache:
**sudo apt-get install apache**

Enjoy!

---

