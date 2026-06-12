---
title: "where's the source code?"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by hfshacker on 2006-11-12
How do I download the sourcecode? I know I can type "apt-get source " and then a package but I can't find a valid name for a package. (*,)

---

### Post by goatflyer on 2006-11-12
Which program do you want source for?  Most programs have their own webpages where you can get source for the most up-to-the-minute latest. greatest, freshest bugs.

If you just want to read the kernel source online for study purposes, visit:

[http://lxr.linux.no/](http://lxr.linux.no/)

they have a good system of cross-referencing links.



good luck

---

### Post by calum on 2006-12-03
> **hfshacker said:**
> How do I download the sourcecode? I know I can type "apt-get source " and then a package but I can't find a valid name for a package. (*,)


Running "dpkg -S <filename>" in a terminal will tell you what (binary) package installed a particular filename, if that's any help...

---

