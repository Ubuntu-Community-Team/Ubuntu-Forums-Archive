---
title: "need help setting up bluetooth"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-08-16
I am trying to get bluetooth working on my Dell Inspiron e1505 laptop, but have been unable to detect the device. I have it enabled through bios, but the little light has never come on. Here are my results when I try to connect my device:

scott@scott-laptop:~$ sudo /etc/init.d/bluetooth restart
Password:
 * Restarting Bluetooth services                                         [ OK ] 
scott@scott-laptop:~$ hcitool dev
Devices:
scott@scott-laptop:~$ hcitool scan
Device is not available: No such device

Any help will be greatly appreciated.

---

### Post by grimmoner on 2007-08-16
does "hciconfig" make any output???

if yes, do an
hciconfig hci0 up

maybe the device name is different to you.

---

### Post by rouge568 on 2007-08-16
no output for hciconfig

---

