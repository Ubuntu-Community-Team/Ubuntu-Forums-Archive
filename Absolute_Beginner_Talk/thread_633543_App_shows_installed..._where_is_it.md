---
title: "App shows installed... where is it"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by LarryJ2 on 2007-12-06
I read just heard about the Data Execution Prevention (DEP)  processor flag bit and then heard about AppArmor.

On my pc, Adept Manager shows apparmor and apparmor-utils are installed. But where are they and how do I access them?  For example, 

sudo find / -name apparmor shows a list of programs but nothing in /sbin or /bin.

sudo find / -name apparmor-utils  shows a directory /usr/share/doc/apparmor-utils but it is empty of help files.

There's nothing in any of my system or utilities menus that resembles  the spelling of apparmor. 

Wouldn't it be sensible for AdeptManager to show the installed location of programs as it installs them?  I don't see any way to configure or verify that apparmor is installed.

Larry

---

### Post by oldos2er on 2007-12-06
Type 'info apparmor' in a terminal.

---

### Post by LarryJ2 on 2007-12-07
> **oldos2er said:**
> Type 'info apparmor' in a terminal.

Also for benefit of others who arrived here by search:

Try [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

and 

[http://en.opensuse.org/Apparmor](http://en.opensuse.org/Apparmor)

For example you can get status from
```
sudo /etc/init.d/apparmor status
```

Interesting articles about apparmor can be found  in the
 **Press Articles** section near the bottom of the page  on this site:
[http://en.opensuse.org/Apparmor](http://en.opensuse.org/Apparmor)

---

