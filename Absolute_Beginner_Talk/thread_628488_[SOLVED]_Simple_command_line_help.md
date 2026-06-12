---
title: "[SOLVED] Simple command line help"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2007-12-01
Hi guys
I'm looking for a couple of commands to probe hardware information. I'm helping a friend over the phone and i'm trying to find out her specs.
Thanks
Shane

---

### Post by bingoUV on 2007-12-01
RAM : ```
 cat /proc/meminfo 
```  CPU :  ```
 cat /proc/cpuinfo 
```  PCI (LAN, sound, network, graphics etc.) ```
 /sbin/lspci 
```  USB stuff ```
 /sbin/lsusb 
```

---

### Post by DutyDuty on 2007-12-01
```
lspci
``` is the best-known. There's also one which involved the term "Xorg" but it escapes me. 

Do a search and you should find it.

---

### Post by arochester on 2007-12-01
See [http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/](http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/)

---

### Post by Hospadar on 2007-12-01
lsusb

---

### Post by slibuntu on 2007-12-01
Thats great guys, thanks a mill.

---

