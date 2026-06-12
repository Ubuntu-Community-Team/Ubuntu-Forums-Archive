---
title: "Edit read only file"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by JasonWard on 2007-03-21
This [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/extra-repositories.html) tells me to edit "etc/apt/sources.list" unfortunately doesn't tell me how to save the file once I've edited it.

GEdit reports "Could not save the file /etc/apt/sources.list.  You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

What do I do now?

Jason
:confused:

---

### Post by Bachstelze on 2007-03-21
You are not in Windows anymore ;) System files are protected so only the super-user (aka "root" can edit them. To learn how to run programs with root privileges, see [here](https://wiki.ubuntu.com/RootSudo).

---

### Post by bruce89 on 2007-03-21
```
gksudo gedit /etc/apt/sources.list
```

> **JasonWard said:**
> Could not save the file /etc/apt/sources.list. You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

Looks as if I am going to have to file a bug about that grammar.

---

### Post by JasonWard on 2007-03-21
Thanks, that worked.

As for not being on Windows, you are not kidding, I like ubuntu, and its several orders of magnitude easier to use than other distros I've tried over the years, but I still find it intimidating and the documentation incomplete.

Oh well, its getting better all the time.

Jason

---

