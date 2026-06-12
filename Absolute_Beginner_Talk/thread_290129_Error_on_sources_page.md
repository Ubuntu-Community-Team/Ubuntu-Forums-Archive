---
title: "Error on sources page"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by gowron69 on 2006-10-31
Im having problems with my sources.list page.  At some time I guess I made a mistake in installing one of my programs and the sources.list page got messed up because now when I attempt to install it gives me an error message like my current one which is error on line 28 I'm new to ubuntu so this is quite frustrating.  How do I reset this page to a default mode or something?

---

### Post by dmizer on 2006-10-31
do this at the command line:
```
gksudo gedit /etc/apt/sources.list
```
and look for line 28.  see if you can determine what the problem is by looking at it.  if not, post the contents here (please be sure to use [code] or [quote] tags).

---

