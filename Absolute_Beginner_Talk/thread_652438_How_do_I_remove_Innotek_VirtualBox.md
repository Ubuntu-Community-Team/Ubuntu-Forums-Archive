---
title: "How do I remove Innotek VirtualBox"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-28
How can I remove Innotek Virtualbox please.

---

### Post by markharding557 on 2007-12-28
assuming you installed it from repositorys or a deb from their web site you can uninstall it in synaptic

---

### Post by spydon on 2007-12-28
You can also write
```
sudo apt-get remove virtualbox-ose
```
in a terminal if you think that is easier.

---

### Post by a.v.l on 2007-12-28
> **markharding557 said:**
> assuming you installed it from repositorys or a deb from their web site you can uninstall it in synaptic

Thanks, that worked fine.

---

### Post by a.v.l on 2007-12-28
> **spydon said:**
> You can also write
```
sudo apt-get remove virtualbox-ose
```
in a terminal if you think that is easier.

Thank you too, I tried this method first, but had the terminal reply that the package couldn't be found.

---

### Post by hodenkat on 2008-05-03
I want to uninstall Inotek VirtualBox too.
I've been hammering away at it for two days trying to get it to work and I've finally had enough.

virtualbox-ose is something else and yes it can be uninstalled in add-remove programs. Innotek's version is something else.

---

### Post by hodenkat on 2008-05-03
In synaptic package manager, do a search for "virtualbox".
Look for virtualbox with it's checkbox checked. It will have the version to the right.

Click on it and choose to "Mark for complete removal".
Click apply...done!

---

