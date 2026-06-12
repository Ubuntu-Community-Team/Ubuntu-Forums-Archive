---
title: "Asus G74S Mouse Driver"
date: 2011-12-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kpryde on 2011-12-08
My mouse keeps not working and Asus claims there are drivers out there that will fix it, but refuses to tell me where they are so I can fix the problem. My external mouse will sporadically work, and my touchpad not at all. Does anyone know where these mouse drivers can be found? I am running Ubuntu 11.10.

---

### Post by Synoc on 2011-12-09
what is your mouse? ASUS may not have a driver for one. most mouse drivers are generic and it surprises me at this day and age that a mouse is not autodetected save for the mice owned by the WoW gaming crowd with their 15 buttons on them... 

jsut for kicks give us the output of
```
 lsusb 
```

assuming it's a USB mouse. the REAL question I don't have an answer to is USB 3. I've never tried... it's not a USB 3 port is it?

---

### Post by kpryde on 2011-12-09
Here it is with two different mice. First a mouse I don't know the brand of, then a lenovo:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004

---

### Post by kpryde on 2011-12-09
Here it is with two different mice. First a mouse I don't know the brand of, then a lenovo:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 1bcf:2885 Sunplus innovation Technology Inc.
Bus 001 Device 005 Id 0bda:0139 Realtek Semiconductor Corp.
Bus 001 Device 006: Id 0cf3:3005 Atheros Communications, Inc.
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

And the Lenovo

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 1bcf:2885 Sunplus innovation Technology Inc.
Bus 001 Device 005 Id 0bda:0139 Realtek Semiconductor Corp.
Bus 001 Device 006: Id 0cf3:3005 Atheros Communications, Inc.
Bus 002 Device 004: ID 04b3:310c IBM Corp. Wheel Mouse


Thanks

---

