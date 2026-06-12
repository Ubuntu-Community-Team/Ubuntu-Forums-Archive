---
title: "usb tv sticks"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by marks321 on 2007-07-01
HI can anybody tell me if i can use my compro VS usb stick with ubuntu. thanks in advance for your help

---

### Post by @trophy on 2007-07-01
> **marks321 said:**
> HI can anybody tell me if i can use my compro VS usb stick with ubuntu. thanks in advance for your help

I just got through setting up a USB capture device... they're a pain.  Anyway it depends on the chipset... plug in the device and then type "lsusb" into the terminal.  It will list out all of your USB stuff, and one of them will be the device.  Post the output of that command here.

---

### Post by marks321 on 2007-07-08
Thanks here is the output

ark@mark-tea:~$ lsusb
Bus 003 Device 003: ID eb1a:2870 eMPIA Technology, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mark@mark-tea:~$

---

### Post by whitebuffalo on 2007-08-23
I'm having the same problem with my ADS Tech videoXpress
here's my lsusb output

Bus 002 Device 042: ID 06e1:a192 ADS Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 039: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 001 Device 001: ID 0000:0000

---

