---
title: "apt-get trouble"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-26
sudo apt-get install iptables
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by kellemes on 2007-09-26
It's probably the automatic-update-manager (that I don't use myself) that's running..
Not sure how this works but I would try to kill it before using apt-get.

---

### Post by Dr Small on 2007-09-26
Do you have Synaptic open ?
You can not have two programs that install software, open at the same time.

Dr Small

---

### Post by Ink-Jet on 2007-09-26
iptables isn't installed by default?

---

### Post by Majorix on 2007-09-26
> **larry Gaminde said:**
> sudo apt-get install iptables
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

iptables is already installed. You don't have to do it again, it will most likely say you have the latest version and do nothing.

And you most likely have another package manager open, like the Update Manager or Synaptic or another CLI running. Close them first before you try to install further programs.

---

### Post by larry Gaminde on 2007-09-26
You were correct synaptic was running but when installing iptables it said it could not be confirmed as a good package.

---

### Post by larry Gaminde on 2007-09-26
Im having trouble with the firewall (I think) and uninstalled iptables,lokkit and firestarter then reinstalled the first 2.

---

