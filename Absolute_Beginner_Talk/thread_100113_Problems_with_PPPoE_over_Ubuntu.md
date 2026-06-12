---
title: "Problems with PPPoE over Ubuntu"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by nubuntux on 2005-12-06
I have an existing WindowsXP dual boot with UBuntu 5.04. PLease help me setup my DSL PPPoE, but i cant trace if that is a DHCP or Static. since i supply a command ipconfig /all and ive have 10.0.0.3, 255.255.255.0 and 10.0.0.1 In Ubuntu part, setting this IPs wont run an Internet connection. since network settings doesnt have an "ADD" button to create new connection for PPPoE. How will i do.....

---

### Post by irifan on 2005-12-06
try:

$ sudo pppoeconf

and have your username and password ready.

---

### Post by nubuntux on 2005-12-07
[QUOTE=irifan]try:

$ sudo pppoeconf

and have your username and password ready.[/QUOTE]


ok. i'll try... thanks

---

### Post by nubuntux on 2005-12-07
[QUOTE=irifan]try:

$ sudo pppoeconf

and have your username and password ready.[/QUOTE]

Thank you! thank you! it works now! a lot of thanks for helping me with this!

---

