---
title: "[SOLVED] having prolem connecting via bluetooth"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by rhanex on 2007-12-26
[B]hi, im having a problem connecting my mouse to my ubuntu. 
heres the comman i used:[/B]
rhanex@X-ZODIA:~$ hcitool scan
Scanning ...
        00:1B:AF:B4:9E:5A       Nokia 6120 classic
        00:0E:9B:DA:BB:2E       INNKDDAVID
        00:50:F2:E8:A3:EA       Microsoft Mouse
rhanex@X-ZODIA:~$ hidd --connect 00:50:F2:E8:A3:EA
HID create error 13 (Permission denied)
**i keep getting this error when i try to connect my mouse, wats up with this?**

---

### Post by rahimveron on 2007-12-26
Its aguess , try sudo hidd --connect 00:50:F2:E8:A3:EA

---

### Post by rhanex on 2007-12-26
rahimveron mate, thanks a lot it works great!

---

