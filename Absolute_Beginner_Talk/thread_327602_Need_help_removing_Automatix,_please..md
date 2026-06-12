---
title: "Need help removing Automatix, please."
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-12-29
I am trying to remove Automatix from my machine but, after trying with both an Uppercase 'A' and a lowercase 'a', I still find it listed and operable at: Applications – System tools.

If someone would tell me what I'm doing wrong here, I'd appreciate it.

Thanks.

~$ sudo apt-get remove Automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Automatix


~$ sudo apt-get remove automatix
Reading package lists... Done
Building dependency tree... Done
Package automatix is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by d3v1ant_0n3 on 2006-12-29
```
sudo apt-get remove automatix2
``` ought to do it.

They changed from Automatix to Automatix2 a while back, but kept the name as Automatix.

---

### Post by L Campbell on 2006-12-29
> **d3v1ant_0n3 said:**
> ```
sudo apt-get remove automatix2
``` ought to do it.

They changed from Automatix to Automatix2 a while back, but kept the name as Automatix.


That was perfect.

Thank you very much.

---

