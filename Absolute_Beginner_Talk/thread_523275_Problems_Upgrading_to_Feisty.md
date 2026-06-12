---
title: "Problems Upgrading to Feisty"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2007-08-11
I have been running Edgy for a while now and finally decided to Upgrade to Feisty. However, when I go to update through update manager, I get an error message that says Error during Update:
```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
```

It also says that the problem probably is with my network connection, but I have checked and everything seems to be running properly, it just wont upgrade. I burned a CD of Feisty also. Is there a way to upgrade from CD without doing a clean install?

---

### Post by zvacet on 2007-08-11
You need alternate CD to do upgrade from CD.You can do fresh install if you have separate home partition.If you don´t have it you can make one

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

You can back up your files lika this
[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

Or if you want to upgrade via net

```
sudo aptitude update
```

to be sure your distro is up-to-date.After that you can do upgrade with upgrade manager.

---

