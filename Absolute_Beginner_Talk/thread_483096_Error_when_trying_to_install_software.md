---
title: "Error when trying to install software"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by davenom on 2007-06-24
i get the following error when i try to install some new software

[IMG]http://img160.imageshack.us/img160/4356/errorex7.jpg[/IMG]

How exaclty do i fix it?

Thanks

---

### Post by w4ett on 2007-06-24
Your package manager is broken....try thiis:

sudo dpkg --configure -a

sudo mv -f /var/lib/dpkg/status /var/lib/dpkg/status_backup

sudo mv -f /var/lib/dpkg/status-old /var/lib/dpkg/status

sudo apt-get update



If this doesn't work, a reinstall will be required

---

