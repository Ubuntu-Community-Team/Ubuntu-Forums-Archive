---
title: "I use ubuntu kernel is 2.6.20 but can't install windriver , Can you help me ?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by riquelme on 2007-08-24
1.when i write ./configure 
   Result 

root@thanon-desktop:/home/thanon/down1/winDriver/redist# ./configure
loading cache ./config.cache
./configure: 531: Syntax error: "(" unexpected



I don't know why it error. Can you help me please?

Best regards,thanon

---

### Post by sad_iq on 2007-08-24
Try installing build essential and see is ¡f that works...if not post the output of ./configure!!!
  ```
sudo aptitude install build-essential
```

---

### Post by riquelme on 2007-08-24
I  do work follow your already but i can't install WinDriver  becuase old problem .

root@thanon-desktop:/home/thanon/down1/winDriver/redist# ./configure
loading cache ./config.cache
./configure: 531: Syntax error: "(" unexpected

---

### Post by sad_iq on 2007-08-24
Ok...let's see...what is the WinDriver for?? (modem??)...can you post the link where you got that driver(so I can look into it)??

---

### Post by asmoore82 on 2007-08-24
the 'configure' script **that came with the package** contains a **syntax error**.

you are trying to install a **broken** package.

---

### Post by riquelme on 2007-08-24
I want write device driver for PCI CARD

---

### Post by mlentink on 2007-08-24
I've googled WinDriver and found out that it's supposed to help you do exactly that. But I have also seen that it is proprietary software and that they ask money for it. Might as well ask them for support on what is apparently a botched-up installation script or config file...

---

