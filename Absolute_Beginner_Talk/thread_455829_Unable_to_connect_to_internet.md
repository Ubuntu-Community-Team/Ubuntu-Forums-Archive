---
title: "Unable to connect to internet"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Fuqaha on 2007-05-27
Hi,

Im very new to ubuntu. Im using Intel DG965RY motherboard with NIC 82566DC.

Installing Ubuntu was a breeze, but somehow it wont connect to the internet. I have tried googling, and it seemed to be a problem with NIC 82566DC. None of the sites show any remedy for that. 

Please, i really want to use ubuntu (instead of vista im currently using now). Can anyone help me?

---

### Post by seshomaru samma on 2007-05-27
try this:
open a terminal and run these commands (copy paste them):
```

modprobe e1000
```
```
ifconfig eth0 up
```
```
dhclient eth0
```

if you get any errors - post them here

---

