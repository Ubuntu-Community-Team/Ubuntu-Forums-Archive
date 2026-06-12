---
title: "issue with package system in Kubuntu"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-03-21
I'm trying to do updates and uninstall/add new software, but each time I open add/remove or the update in the toolbar, I continually get this message, even after a reboot.

Another process is using the packaging system database (probably some other Adept application apt-get or aptitude). Please close the other application before using this one.

Except I'm not running anything else, and I don't know how to kill this process that is causing this issue.  I need to run updates and remove  and install some new software but am unable to because of this.

Thanks

---

### Post by spiderbatdad on 2008-03-21
not too sure about kubuntu but you might try```
ps aux | grep synaptic
```You should see a process id right after your user name then sudo kill id#

And: ps aux | grep adept

For example:```
linux@linux-laptop:~$ ps aux | grep adept
linux     9022  0.0  0.0   3000   748 pts/0    R+   23:50   0:00 grep adept
linux@linux-laptop:~$ sudo kill 9022
linux@linux-laptop:~$ 

```

Sounds like a package has not finished compiling however. You might try sudo apt-get install -f  and sudo dpkg --configure -a

---

### Post by brdohman on 2008-03-22
thanks for the help.  I think it was a package that didn't finish installing.  I ran the dpkg, and was able to get things to work again.  The other code wll be useful for future though.
Thanks

---

