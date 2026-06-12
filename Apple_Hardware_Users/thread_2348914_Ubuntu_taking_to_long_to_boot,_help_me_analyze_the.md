---
title: "Ubuntu taking to long to boot, help me analyze the problem"
date: 2017-01-09
forum: Apple Hardware Users
---

### Post by williepabon on 2017-01-09
Hi:
Over time, my machine has been increasing boot times. Now, it is taking more than a Win10 laptop I have.  I will really appreciate any advice that will help to reduce boot times. Here is the information of my pc and part of the boot time report I obtained.

```
williepabon@WP-Macmini:~$ lsb_release -crid
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
williepabon@WP-Macmini:~$ uname -a
Linux WP-Macmini 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
Part of the boot time report is:

```
williepabon@WP-Macmini:~$ systemd-analyze blame
         29.859s ModemManager.service
         24.674s grub-common.service
         24.054s apport.service
         23.951s systemd-logind.service
         23.751s console-kit-log-system-start.service
         23.601s rsyslog.service
         23.589s iio-sensor-proxy.service
         19.292s dev-sda5.device
         11.452s apparmor.service
         11.346s nmbd.service
         11.311s winbind.service
         10.836s NetworkManager-wait-online.service
         10.629s samba-ad-dc.service

```

Again, any help/advice to solve this will be appreciated. Thanks
wp

---

### Post by ajgreeny on 2017-01-09
The line **iio-sensor-proxy.service** in your systemd output makes me wonder if this is a proxy connection problem, but unfortunately I can't tell you how to deal with that.
What are your network settings?

---

### Post by ajgreeny on 2017-01-09
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

---

### Post by williepabon on 2017-01-09
ajgreeny:

> [COLOR=#000000]What are your network settings?[/COLOR]

Hope url below answers your question.

[https://drive.google.com/open?id=0B_ZOUN6JcLCXNXlNbnhRejVIdjg](https://drive.google.com/open?id=0B_ZOUN6JcLCXNXlNbnhRejVIdjg)

---

