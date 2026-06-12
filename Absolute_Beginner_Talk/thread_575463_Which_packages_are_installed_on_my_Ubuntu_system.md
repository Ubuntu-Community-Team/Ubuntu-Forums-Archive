---
title: "Which packages are installed on my Ubuntu system"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-10-14
Hi,
I would like to uninstall Ubuntu 7.04 and fresh install Ubuntu 7.10. But on top of base system I have installed several packages, for example Microsoft fonts, etc.

How to get list of manually installed packages on Ubuntu 7.04? And how to install all packages on list with one single command on Ubuntu 7.10?
Thanks,
Abcuser

---

### Post by Beggar on 2007-10-14
To generate a log file of all packages installed:

```
dpkg --get-selections > backup.log
```

copy that file somewhere safe. After the update run:

```
dpkg --set-selections < backup.log
```

to set all the selections, then run 

```
dselect
```

to install the packages, there is an option to "install wanted packages" or something similar.

---

### Post by philinux on 2007-10-14
Read this too.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

---

