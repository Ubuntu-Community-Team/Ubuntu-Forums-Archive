---
title: "Adding Identical Printers (cupsys)"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Stew3975 on 2007-02-10
I have recently installed Ubuntu server (Dapper Drake) to act as a print server for the network at my work place.

The problem I'm having is that the 2 printers we have are identical machines, Samsung ML-1510's.
 
#lpinfo -v 
network socket
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct usb://Samsung/ML-1510_700
direct usb://Samsung/ML-1510_700

Using  lpadmin -E -p [printerName] -v usb://Samsung/ML-1510_700 how do I distinguish bewteen the 2 printers. Thanks in advance. Stewart

---

