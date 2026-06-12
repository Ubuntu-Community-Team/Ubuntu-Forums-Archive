---
title: "HELP!!! automatix guarddog"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by linuxnewbie946 on 2006-07-18
I started guarddog after I installed it through automatix. I configured it and clicked apply. It kept coming up with this error message: 
> FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

Whats the problem?

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **linuxnewbie946 said:**
> I started guarddog after I installed it through automatix. I configured it and clicked apply. It kept coming up with this error message: 


Whats the problem?

Can you give some basic info ? (kernel version, computer type, computer, specs) It seems to be a kernel error on account of iptables support not selected/not working this problem used to exist on Breezy when an upgraded kernel is used. Here is the most logical answer to the problem: You are using a version of iptables that is too new so basically when guarddog tries to change it's policy, it can't.

---

### Post by linuxnewbie946 on 2006-07-18
Kernel -2.6.17.6
Processor -Intel Pentium 4
Memory -497 mb
 PS I cannot uninstall it because of the error

---

### Post by linuxnewbie946 on 2006-07-18
I have an idea. I will reboot the system into an older kernel and try to uninstall it. Wish me luck!

---

### Post by linuxnewbie946 on 2006-07-18
IT WORKED! Guarddog in now uninstalled! Thanks for your help!

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **linuxnewbie946 said:**
> IT WORKED! Guarddog in now uninstalled! Thanks for your help!

No problem, I'm glad I could help.

---

