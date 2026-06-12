---
title: "how can i know the version of the software"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-13
i want to fine the scons verison wht iam using in my ubuntu system
how can i know which command i should use 
thank u
sree

---

### Post by DeHorde on 2007-08-13
You could look at the version numbers displayed in **System > Administration > Synaptic Package Manager** or on the command line do: **apt-cache show <yourpackagename>**

That is provided you used the apt-get system to install the software. Most of the time, 
**$ <yourprogramname> --version** (or maybe** --help** first) on the command line also works.

---

### Post by arochester on 2007-08-13
cat /etc/issue

---

### Post by schorsch on 2007-08-13
Type
```
scons -v
```
in a terminal window.

---

