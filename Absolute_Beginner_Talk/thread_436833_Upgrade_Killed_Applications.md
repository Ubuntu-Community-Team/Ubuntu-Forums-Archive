---
title: "Upgrade Killed Applications"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by shdawson on 2007-05-08
Hi,

Recently upgraded from Server 6.10  Apache, MySQL, and a host of other applications were removed.  I was amazed.  Never in my life have I done an upgrade and applications were removed.

Why did this happen?  How can I prevent this from happening again?  I did run:
[http://www.ubuntu.com/getubuntu/upgrading#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf](http://www.ubuntu.com/getubuntu/upgrading#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf)

I am very scared of any future updating until I can understand how to control this so it does not remove applications again.

HELP!!!!!

---

### Post by Seisen on 2007-05-08
Normally it doesn't remove them. Did you use Synaptic or apt-get to install them or did you install them a different way?

---

### Post by shdawson on 2007-05-08
I followed [http://www.ubuntu.com/getubuntu/upgrading#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf](http://www.ubuntu.com/getubuntu/upgrading#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf)

sudo apt-get install update-manager-core

sudo do-release-upgrade

---

### Post by Seisen on 2007-05-08
What I meant was did you install MySQL and the other applications with synpatic or apt-get or did you install them some other way. Its my fault for not being explaining my question better.

---

### Post by shdawson on 2007-05-08
They were installed as part of the Server 6.10 installation.

---

### Post by shdawson on 2007-05-09
Help !!!!!

---

### Post by bobplano on 2007-05-09
isn't there an option to install a LAMP server on the live cd? just use that option again

---

### Post by shdawson on 2007-05-10
No, that option is not availlable. This machine does not work well with the Live CD.  RAM.

Regardless, how can I control what applications get removed in future upgrades?

---

