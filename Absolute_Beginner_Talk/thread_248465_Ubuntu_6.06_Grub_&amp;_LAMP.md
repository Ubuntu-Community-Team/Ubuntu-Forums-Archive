---
title: "Ubuntu 6.06 Grub &amp; LAMP"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by doodsangel on 2006-09-01
Goo Day,

I need help. I installed Ubuntu, and then windows installation corrupted due to a corrupt MBR. So I re-installed Windows.. I need now to fix up my GRUB, so that I can get into my UBUNTU installation.

1. Is there any easy way to do this, or should I just do a complete reinstall of UBUNTU?

I also need to do a lamp install on my UBUNTU Desktop installation.

2.1. If I select UBUNTU server from the install CD, will it wipe my UBUNTU desktop?
2.2. If I'd like to install LAMP on Desktop if 2.1 wipes out desktop, how would I go about it.
2.3. Internet not up on UBUNTU box yet, so if I need to download packages, which ones are the ones that I need, as there is 100s of PHP, MYSQL and Apache packages.

Thanks.

---

### Post by eternalis on 2006-09-01
Check this link on restoring GRUB:
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by MrHorus on 2006-09-01
> **doodsangel said:**
> 
2.1. If I select UBUNTU server from the install CD, will it wipe my UBUNTU desktop?


Most likely and if it doesn't, I wouldn't be happy doing a new install on top of an old one unless I wiped the drive.

> 2.2. If I'd like to install LAMP on Desktop if 2.1 wipes out desktop, how would I go about it.

```
sudo apt-get install php5 apache2 mysql-server
```[/quote]

> 2.3. Internet not up on UBUNTU box yet, so if I need to download packages, which ones are the ones that I need, as there is 100s of PHP, MYSQL and Apache packages.

Pass - i've always installed them from source or from repos.

---

### Post by doodsangel on 2006-09-01
Thanks.... Will try that tonight.... Thanks....

---

