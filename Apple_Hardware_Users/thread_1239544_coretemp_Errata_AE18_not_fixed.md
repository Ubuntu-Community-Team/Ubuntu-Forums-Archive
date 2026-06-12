---
title: "coretemp Errata AE18 not fixed"
date: 2009-08-13
forum: Apple Hardware Users
---

### Post by mire on 2009-08-13
I have found the cure for this error on the MacbookPro1,1:

> 
[   11.413331] coretemp coretemp.0: Errata AE18 not fixed, update BIOS or microcode of the CPU!
[   11.413379] coretemp coretemp.1: Errata AE18 not fixed, update BIOS or microcode of the CPU!
This is an excerpt from the dmesg output on my machine prior to fixing it. This happens when Intel's microcode update module is either not installed or not loaded before the coretemp module. Once this is installed put the following into  /etc/rc.local. 

```
 modprobe coretemp 
```This will load it after the microcode module is install.

The easiest way to edit this file is to type the following at the terminal.
```
kdesudo kate /etc/rc.local &
```This will enable two CPU temperature sensors.

---

