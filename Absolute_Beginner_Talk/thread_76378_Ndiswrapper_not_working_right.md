---
title: "Ndiswrapper not working right"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by ralin on 2005-10-15
so i figured out how to load drivers into ndiswrapper and then i type in 

depmod -a
modprobe ndiswrapper

and nothing happens, there are no messages in the system log and iwconfig still turns up nothing. 

im trying to install a "linksys wireless-g pci adapter with speedbooster" and im trying to use the 64 bit ubuntu so im using the 64bit driver i got from planetamd64 called Linksys_WMP54G_x64

any help is much apriciated

---

### Post by towsonu2003 on 2005-11-24
try ```
sudo modprobe ndiswrapper
```

---

