---
title: "What permissions to choose ideally for Apache_"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-04-17
Hi,

currently my apache2 folder has 755 permission. What permission setting do you recommend to prevent security breaches?


ben@ben-desktop:~$ ls -l /var/www
total 8
drwxr-xr-x 2 root root 4096 2008-04-17 17:32 apache2-default


thx,
ben

---

### Post by spiderbatdad on 2008-04-17
Those are correct permissions I believe. Security is improved by changing the root directory in sites-available-yoursite to your home directory...and greatly improved by chrooting the server...
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

