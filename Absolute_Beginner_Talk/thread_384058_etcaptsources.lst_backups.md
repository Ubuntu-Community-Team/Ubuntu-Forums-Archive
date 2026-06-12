---
title: "/etc/apt/sources.lst backups"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-14
I was looking in my /etc/apt file and found that my sources.lst file had been automatically backed up by some application it looks like this:

charles@charles-laptop:/etc/apt$ ls
apt.conf                          sources.list_backup_200612101220
apt.conf.d                        sources.list_backup_200612111503
secring.gpg                       sources.list_backup_200702102352
sources.list                      sources.list_backup_200702132201
sources.list_backup_200612071733  sources.list.d
sources.list_backup_200612071917  sources.list.save
sources.list_backup_200612071926  trustdb.gpg
sources.list_backup_200612082256  trusted.gpg
sources.list_backup_200612082324  trusted.gpg~
**This is not the full ls of the file but you get the idea...

I know I did not make those backups does anyone know what did it, don't get me wrong I was actually going to back up my file anyway but what app did it???

---

### Post by chuckyp on 2007-03-14
Maybe if on those dates you changed which repositories were enabled in Administration > Software Sources?   Or possibly you used a scripting that installs binary drivers from so other location.  Like easyubuntu or automatix or even envy scripting.

---

### Post by aidanr on 2007-03-14
automatix makes those backups

---

### Post by charles.g.moore on 2007-03-14
I did use automatix to get some stuff up and running, I guess that makes sense...

Thanks for the quick reply...

---

