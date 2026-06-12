---
title: "help with bluetooth"
date: 2004-12-30
forum: Apple PPC Users
---

### Post by ubuntu4everyone on 2004-12-30
I have a powerbook g4 with intergrated bluetooth, how do i get bluetooth to work on linux?

---

### Post by Johan on 2004-12-30
Start with loading some modules by
```
modprobe rfcomm
```
```
modprobe bluetooth
```
```
modprobe hci_usb
```
To see if it worked, type
```
hciconfig
```
and if you're lucky it lists an interface.

---

### Post by ubuntu4everyone on 2004-12-31
Hi
It says stuff about type and bd addresses however in type it says usb but my one is intergrated is this ok. and if it is then how do i start pairing etc

---

### Post by tiiim on 2005-01-02
yeah i like to know i got intergrated bluetooth too...

---

