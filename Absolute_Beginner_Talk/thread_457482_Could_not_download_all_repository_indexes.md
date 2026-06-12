---
title: "Could not download all repository indexes"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-28
hey guys! I've been using Ubuntu Feisty now for about a week and it's working great

I recently had some java issues and decided to reinstall ubuntu, it's worked and I no longer have that specific issue.

however... now when i try to install anything java related from the add/remove programs list, it gives me this error 

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


what should i do?

---

### Post by taurus on 2007-05-28
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

