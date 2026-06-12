---
title: "how I can un-install a package that I installed from a repo?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-21
Hi
Thank you for reading my post
I have installed some packages from a repo using apt-get install command, now I want to uninstall it, what should i do?
Is it possible to un-install them safely?

Thanks

---

### Post by OffAxis on 2008-01-21
```
sudo apt-get remove [package name]
```

---

### Post by PeterJS on 2008-01-21
> **legolas_w said:**
> Hi
Thank you for reading my post
I have installed some packages from a repo using apt-get install command, now I want to uninstall it, what should i do?
Is it possible to un-install them safely?

Thanks

The complement to apt-get install is apt-get remove. You can also remove them using synaptic.

---

### Post by Cypher on 2008-01-21
Also run "apt-get autoremove" when you've installed a few packages to see if there are any other unused common files that weren't explicitly removed..

---

### Post by gerscht on 2008-01-21
```
apt-get remove packagename
```
will remove the package only and leave the configuration files  (like in /etc or your /home).
If you reinstall the package, it will use the same configuration.
```
apt-get purge packagename
```
will remove the configuration as well.

---

