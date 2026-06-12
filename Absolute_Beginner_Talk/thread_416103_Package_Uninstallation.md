---
title: "Package Uninstallation"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by niglch on 2007-04-20
This is just a general question about uninstalling packages on Ubuntu. If you install a package with specific dependencies which are also installed and later uninstall it, will the dependent packages also be removed if they are not depended upon by any other packages? If not, is there a way to remove unused packages like this?

---

### Post by chamberlain2006 on 2007-04-20
You can use the "sudo apt-get autoremove" command.  If there are packages that were installed as dependencies, it will let you know that you can remove them.

---

### Post by johnc4510 on 2007-04-20
Here is a good page on installing and why you should use aptitude in the command line for installations of packages. Note. this web site has a lot of very good help on it for new Ubuntu users:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

