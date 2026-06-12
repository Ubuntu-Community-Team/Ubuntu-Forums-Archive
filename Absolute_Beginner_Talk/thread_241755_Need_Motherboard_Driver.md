---
title: "Need Motherboard Driver"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by mspear on 2006-08-22
I need a motherboard driver for a machspeed k8m8ms or k8m8m. My network card doesn't work so i need to get that driver for it to work.

---

### Post by arsenic23 on 2006-08-22
That board should have a Intergrated Realtek 8100C network solution....  
I'm not 100% but I'm fairly sure that it should just work out of the box in Ubuntu.

Does a REalteck 8100C come up on the list that is generated when you type lspci into the terminal ?

---

### Post by mspear on 2006-08-22
yeah, it came up, so it has a driver then?

---

### Post by arsenic23 on 2006-08-23
I am vaguely sure that it should just work... and since no one more knowlegeable has come along to help lets see what we can do.

If you type ifconfig into the terminal it should so all your network interfaces and how they are configured.  Let's see if yours shows up.

Should look something like:
> eth0      Link encap:Ethernet  HWaddr ***************
          [INDENT]inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ******************** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31696443 (30.2 MiB)  TX bytes:1671695 (1.5 MiB)
          Interrupt:58 Base address:0x2000[/INDENT]

lo        Link encap:Local Loopback
          [INDENT]inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)[/INDENT]


If it does show up here then it doesn't need a driver, it just needs to be configured propperly.  If you don't have a network icon on a panel yet, you can do this by rightclicking an empty spot on a panel, clicking 'Add Pannel', and then adding the "Network Monitor". ( I'm asuming your running Gnome here - this'll be different if you using KDE or something else. )

---

