---
title: "Need some more help"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by denfoote on 2006-07-26
I'm trying to use dpkg to remove an application that was interupted by a power outage.

This is what I get when I try to use it:

> Options marked [*] produce a lot of output - pipe it through `less' or `more' !
denfoote@denfoote-desktop:~$ dselect
running dpkg --pending --remove ...
dpkg: requested operation requires superuser privilege

What is superuser privilege??


Here is the error message I'm getting when I try to uninstall the application.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Help!!!! :confused:

---

### Post by abowman on 2006-07-26
Did you try:
```

sudo dpkg -r package_name

```

---

### Post by denfoote on 2006-07-26
No, but I will!!

---

### Post by denfoote on 2006-07-26
> dpkg - warning: ignoring request to remove macromedia which isn't installed.


Of course the package was not installed!! The power went out while I was downloading the bloody thing!!

---

