---
title: "vnc's problem!!"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by yusy on 2006-07-25
OS:ubuntu 6.06
I installed a xven4viewer.
:~$ xvnc4viewer

Tue Jul 25 16:22:36 2006
 main:        unable to connect to host: No route to host (113)
:~$

but , the sever is in the same subnet.
sever's ip is 192.168.2.3
and sever's OS is FC5.
client's ip is  192.168.2.2

route table is :
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by ape on 2006-07-25
Can you ping 192.168.2.3 from the client?

Is vncserver running on 192.168.25.3?

In the example below you didn't supply a target host (such as 'xvnc4viewer 192.168.2.3:1').  Do you get the same error if you add this (or was your information a typo)?

---

