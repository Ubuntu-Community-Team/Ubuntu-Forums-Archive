---
title: "File Systems Might Become Read-Only with ext3"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by UlfA on 2007-09-26
When running in VMWare the filesystem can go read-only at times.

For RH and SUse there are RPM patches and VMWare has following link for solution:

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=51306](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=51306)

I was wondering if there is an ubuntu fix or if the best way is to try and convert the rpm to a dpkg?

---

### Post by jfinkels on 2007-09-27
Is this problem occurring to you?

There are other virtualization software applications out there, see VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/) for example.

If you want to convert a .rpm to a .deb package, you can use the program "alien". Install alien by typing the following in a terminal:```
sudo aptitude install alien
``` Run alien by typing the following:```
alien -c -d *filename.rpm*
``` Read more about alien by typing the following in the terminal:```
man alien
``` To install a .deb package, type the following in the terminal:```
sudo dpkg -i *filename.deb*
```

---

