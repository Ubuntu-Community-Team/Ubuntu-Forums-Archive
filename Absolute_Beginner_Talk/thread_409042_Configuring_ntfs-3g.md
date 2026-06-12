---
title: "Configuring ntfs-3g"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-14
I've installed ntfs-3g into Ubuntu 6.06, but say's it's not configured. Anyone know how to fix this? Thanks.

---

### Post by Rospo Zoppo on 2007-04-14
Have you installed the graphic tool or the drivers only?

---

### Post by huygens on 2007-04-14
You can find all the information you need to install ntfs-3g on Ubuntu 6.06 in the official community documentation: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Just to make things clear: for Ubuntu 6.06 (a.k.a. Dapper Drake) 3 different repositories are proposed, you only need to take one of them that's enough. The first one is a good one ;-) the other too.
As you are on Ubuntu 6.06 once you added the extra repository, you need to check your system for update (else the ntfs-3g installation will fail). So execute (just as stated in the document):
```
sudo apt-get update
sudo apt-get upgrade
```After that you can install ntfs-3g (or ntfs-config, and you get a really simple and effective window which will enable NTFS write for you).

---

