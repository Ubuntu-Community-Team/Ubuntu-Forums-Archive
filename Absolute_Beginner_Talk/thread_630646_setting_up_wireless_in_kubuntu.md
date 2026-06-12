---
title: "setting up wireless in kubuntu"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-03
I am pretty sure that I got my drivers installed properly, now what is the software that I use for scanning for wireless networks?  I am using Kubuntu

---

### Post by Sarteck on 2007-12-03
Well, if you don't already know the network you are connecting to, I guess you can use KWLAN Manager, or the number of other Wireless/WiFi managers/tools under the "Internet" section when using the "Add/Remove Programs" bit in your K Menu.

---

### Post by Dapman01 on 2007-12-03
Is KWLAN already installed.  I can't get kubuntu on the internet right now

---

### Post by Sarteck on 2007-12-03
Ah.  No.  Heh.

If you use your System Settings and go to the Network panel, you can enter the network information there, if you know it.  As for scanning...  Argh.  There was a command-line program that did it, but I can't remember it at the moment....

---

### Post by OffAxis on 2007-12-03
```
iwlist [eth0] scan
```

where 
eth0 = your network card

---

