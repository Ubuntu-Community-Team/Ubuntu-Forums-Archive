---
title: "i have small problem with my wireless"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by programmer in linux on 2007-02-02
hello all

i can`t connect to the internet if i put password in my network

so how i can enter the password in terminal to connect to the internet with my security network 

can anyone help

---

### Post by gustolove on 2007-02-02
are you going to use WEP or WPA?

if it is wep then type:

"sudo iwconfig <device name> essid <network name> enc <password/encryption>"**






**without the ""s or the <>s

---

### Post by programmer in linux on 2007-02-02
thx

but i use WPA

---

### Post by pegazuz on 2007-02-02
> **programmer in linux said:**
> thx

but i use WPA

I used KnetworkManager under Kubuntu to connect to my secure wireless network.  It gives you several different options including WPA, password etc.

---

