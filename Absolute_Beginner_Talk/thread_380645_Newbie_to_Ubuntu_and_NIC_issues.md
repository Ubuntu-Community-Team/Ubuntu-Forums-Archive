---
title: "Newbie to Ubuntu and NIC issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by MrSoxs on 2007-03-09
<I have posted this in networking section if a mod can delete it for me please!>

Hi Guys, 

I have a system running Ubuntu, i want to turn it into a Firewall server so i went out and got myself another Realtek 8139 10/100 NIC for the pc.  I installed it but the device manager is saying UNKNOWN DEVICE?  If its the same as teh other NIC thats allready installed and working how can ubuntu not know what it is?  

Can anyone tell me what i can do to get the 2nd NIC working?

Cheers

---

### Post by zubrug on 2007-03-09
Does it show up in networking or hardware / system devices?

---

### Post by MrSoxs on 2007-03-09
It shows up as Unknown (0x8539) in device manager but nothing else.  Networknig and Network Tools only shows my first NIC???:(

---

### Post by zubrug on 2007-03-09
type ifconfig in the terminal and post what it reply's

---

### Post by MrSoxs on 2007-03-09
> **zubrug said:**
> type ifconfig in the terminal and post what it reply's

eth0      Link encap:Ethernet  HWaddr 00:E0:4D:3A:42:BC
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe3a:42bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41348 (40.3 KiB)  TX bytes:20591 (20.1 KiB)
          Interrupt:21 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1703994 (1.6 MiB)  TX bytes:1703994 (1.6 MiB)

---

### Post by zubrug on 2007-03-09
[http://www.ubuntuforums.org/showthread.php?t=378857&highlight=two+network+cards](http://www.ubuntuforums.org/showthread.php?t=378857&highlight=two+network+cards)

try here

---

### Post by MrSoxs on 2007-03-09
Cool, but the only thing is it doesnt even give me a working device so i can edit or change any .conf if the device is not starting???:(

---

