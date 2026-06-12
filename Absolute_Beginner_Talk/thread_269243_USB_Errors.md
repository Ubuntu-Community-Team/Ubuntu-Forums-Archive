---
title: "USB Errors"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-10-01
So I've been having problems with using BitPim because my usb ports are acting funny. 

I Created /etc/udev/rules.d/60-cell.rules

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
# LG Phone
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", MODE="0666"
LABEL="cell_rules_end"


But my computer still couldn't detect my usb device so I manually set it to: /dev/ttyACM0. Now when I try to export information to the usb device I get this error:

/dev/ttyACM0: could not open port:[Errno 13] Permission denied:/'dev/

Why does BitPim keep denying me? :mad:

---

### Post by qscgz on 2006-10-31
?

Sorry I'm not very deep into this stuff. May be you find the proper search term and use [https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage)

---

