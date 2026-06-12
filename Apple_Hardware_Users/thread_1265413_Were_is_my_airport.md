---
title: "Were is my airport?"
date: 2009-09-13
forum: Apple Hardware Users
---

### Post by Plantaginus on 2009-09-13
Hi.

How to setup my wireless network? 

Thanks.

---

### Post by gwydionwaters on 2009-09-15
hey, just got mine working. go to this [link]("http://linuxwireless.org/en/users/Drivers/b43#device_firmware"), then scroll to 
**You are using the b43 driver from linux-2.6.25 or newer**

*note some instructions are unnecessary/left out ... afte make, type make install.
* omit the export path in the second part and where it says ```

../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```you can just type ```
b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```follow the instructions there, then in a terminal type ```
modprobe b43
``` or the same with sudo if you are not currently root. restart, it should be there after that. have you gotten sound up yet?

*i forgot to add, after this edit /etc/rc.local to include ```
modprobe b43
```  :)

---

