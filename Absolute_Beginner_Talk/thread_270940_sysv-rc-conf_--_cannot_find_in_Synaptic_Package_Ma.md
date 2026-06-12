---
title: "sysv-rc-conf -- cannot find in Synaptic Package Manager"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by ted kubaska on 2006-10-04
I read about people using sysv-rc-conf and they say they download it from the repository.

I dont see it there?

If I invoke System--Administration-Services I get a very abbreviated window that looks nothing like the help.

What I want to do is configure my Dapper to automatically start up mysql server on bootup. Currently I do this manually as

```
/usr/local/mysql/bin/mysqld_safe --user=mysql &
```
Thanks

---

### Post by ciscosurfer on 2006-10-04
You need to enable your Universe repository (read here [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html))

Then download it like you normally would via your favorite package manager...use Synaptic (which uses apt), it has a nice graphical user interface which makes it easy to use.

---

