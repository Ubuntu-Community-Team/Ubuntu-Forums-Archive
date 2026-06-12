---
title: "How should I upgrade to 6.06"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by gmatt on 2006-07-13
I am currently running Breezy Badger and I want to upgrade to Dapper Drake. Is there a way I can do it (perhaps through automatic updates) other than reinstall Ubuntu entirely?

---

### Post by lordlollo on 2006-07-13
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

Cheers.

---

### Post by gmatt on 2006-07-13
I get the following error now:

Failed to fetch cdrom:[Ubuntu 5.10 _breezy Badger_ - Preview amd64 (20050908)]/dists/breezy/main/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

What does this mean?

---

### Post by lordlollo on 2006-07-13
When do you get the error messge? Maybe when you try 
```
sudo apt-get update
```
:-k

---

### Post by gmatt on 2006-07-13
I just left a line that should be commented uncommented in my sources.list :S

Problem fixed.

---

